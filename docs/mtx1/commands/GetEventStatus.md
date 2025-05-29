# GetEventStatus

Request/response to get device status events.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x01` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `1`   | `0x01` |
| command size | `0`   | `0x00` |

Command hex dump: `01 00`


## Response

### Format

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x01`                       |
| `1`  | `uint8` | command size = `2`                        |
| `1`  | `uint8` | [status event set 1](#status-event-set-1) |
| `1`  | `uint8` | [status event set 2](#status-event-set-2) |

### Parameters

#### Status event set 1

Bit mask:

| Name                       | Bit | Description                                             |
| -------------------------- | --- | ------------------------------------------------------- |
| `CASE_OPEN`                | `0` | meter enclosure opened                                  |
| `MAGNETIC_ON`              | `1` | detection of constant or alternating magnetic influence |
| `PARAMETERS_UPDATE_REMOTE` | `2` | remote parameter configuration                          |
| `PARAMETERS_UPDATE_LOCAL`  | `3` | local parameter configuration                           |
| `RESTART`                  | `4` | meter program restart                                   |
| `ERROR_ACCESS`             | `5` | invalid password and lockout                            |
| `TIME_SET`                 | `6` | time set                                                |
| `TIME_CORRECT`             | `7` | time correction                                         |

#### Status event set 2

Bit mask:

| Name                        | Bit | Description                                            |
| --------------------------- | --- | ------------------------------------------------------ |
| `DEVICE_FAILURE`            | `0` | meter failure                                          |
| `CASE_TERMINAL_OPEN`        | `1` | meter terminal box opened                              |
| `CASE_MODULE_OPEN`          | `2` | meter module compartment opened                        |
| `TARIFF_TABLE_SET`          | `3` | tariff plan changed                                    |
| `TARIFF_TABLE_GET`          | `4` | new tariff plan received                               |
| `PROTECTION_RESET_EM`       | `5` | electromagnetic interference screen reset (104.23.001) |
| `PROTECTION_RESET_MAGNETIC` | `6` | magnetic interference screen reset (104.23.001)        |

### Examples

| Field              | Value                                                                                                                                                                                                                            | Hex    |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| command id         | `1`                                                                                                                                                                                                                              | `0x01` |
| command size       | `2`                                                                                                                                                                                                                              | `0x02` |
| status event set 1 | `CASE_OPEN`: `true`<br>`MAGNETIC_ON`: `false`<br>`PARAMETERS_UPDATE_REMOTE`: `true`<br>`PARAMETERS_UPDATE_LOCAL`: `false`<br>`RESTART`: `false`<br>`ERROR_ACCESS`: `false`<br>`TIME_SET`: `false`<br>`TIME_CORRECT`: `true`      | `0x85` |
| status event set 2 | `DEVICE_FAILURE`: `false`<br>`CASE_TERMINAL_OPEN`: `false`<br>`CASE_MODULE_OPEN`: `false`<br>`TARIFF_TABLE_SET`: `false`<br>`TARIFF_TABLE_GET`: `true`<br>`PROTECTION_RESET_EM`: `false`<br>`PROTECTION_RESET_MAGNETIC`: `false` | `0x10` |

Command hex dump: `01 02 85 10`


## See also

* [Access level](../basics.md#command-access-level)
