# GetQuality

Request/response to get voltage quality information.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x73`                       |
| `1`  | `uint8` | command size = `2`                        |
| `1`  | `uint8` | year (number of years after `2000`)       |
| `1`  | `uint8` | month (`1` - January ... `12` - December) |

### Examples

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `115`                         | `0x73` |
| command size | `2`                           | `0x02` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |
| month        | `2` (February)                | `0x02` |

Command hex dump: `73 02 18 02`


## Response

### Format

| Size | Type     | Field                                                                                                                                                 |
| ---- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x73`                                                                                                                                   |
| `1`  | `uint8`  | command size = `20`                                                                                                                                   |
| `1`  | `uint8`  | year (number of years after `2000`)                                                                                                                   |
| `1`  | `uint8`  | month (`1` - January ... `12` - December)                                                                                                             |
| `4`  | `uint32` | Total duration of power outages during the month that are greater than or equal to [powerOffTrackingInterval](./SetOperatorParameters.md), in minutes |
| `2`  | `uint16` | Number of power outages during the month that are greater than or equal to [powerOffTrackingInterval](./SetOperatorParameters.md)                     |
| `4`  | `uint32` | Total duration of power outages during the month that are less than [powerOffTrackingInterval](./SetOperatorParameters.md), in minutes                |
| `2`  | `uint16` | Number of power outages during the month that are less than [powerOffTrackingInterval](./SetOperatorParameters.md)                                    |
| `2`  | `uint16` | Total duration of poor voltage quality on phase `A` during the month, in minutes                                                                      |
| `2`  | `uint16` | Total duration of poor voltage quality on phase `B` during the month, in minutes                                                                      |
| `2`  | `uint16` | Total duration of poor voltage quality on phase `C` during the month, in minutes                                                                      |

### Examples

| Field                   | Value    | Hex          |
| ----------------------- | -------- | ------------ |
| command id              | `115`    | `0x73`       |
| command size            | `20`     | `0x14`       |
| year                    | `26`     | `0x1a`       |
| month                   | `1`      | `0x01`       |
| powerOffSaidiMinutes    | `565316` | `0x0008a044` |
| powerOffSaidiCount      | `3`      | `0x0003`     |
| powerOffMaidiMinutes    | `0`      | `0x00000000` |
| powerOffMaifiCount      | `3`      | `0x0003`     |
| badVoltagePhaseAMinutes | `34`     | `0x0022`     |
| badVoltagePhaseBMinutes | `0`      | `0x0000`     |
| badVoltagePhaseCMinutes | `0`      | `0x0000`     |

Command hex dump: `73 20 1a 01 0008a044 0003 00000000 0003 0022 0000 0000`


## See also

* [Access level](../basics.md#command-access-level)
* [Power-off tracking interval](./SetOperatorParameters.md)
