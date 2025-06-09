# GetEventsCounters

Request/response to get counters related to various system events and actions.
Each counter represents the total number of occurrences for a specific type of event or system interaction, such as restarts, power-offs, parameter changes, and access attempts.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x34` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `52`  | `0x34` |
| command size | `0`   | `0x00` |

Command hex dump: `34 00`


## Response

### Format

| Size | Type     | Field                                                       |
| ---- | -------- | ----------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x34`                                         |
| `1`  | `uint8`  | command size = `14`                                         |
| `2`  | `uint16` | number of device restarts                                   |
| `2`  | `uint16` | number of power-off events                                  |
| `2`  | `uint16` | number of local parameter changes                           |
| `2`  | `uint16` | number of remote parameter changes                          |
| `2`  | `uint16` | number of access failures (due to incorrect encryption key) |
| `2`  | `uint16` | number of access blocks caused by frequent access failures  |
| `2`  | `uint16` | number of real-time clock (RTC) changes                     |

### Examples

| Field                                   | Value | Hex      |
| --------------------------------------- | ----- | -------- |
| command id                              | `5`   | `0x34`   |
| command size                            | `14`  | `0x0e`   |
| number of device restarts               | `1`   | `0x0001` |
| number of power-off events              | `2`   | `0x0002` |
| number of local parameter changes       | `3`   | `0x0003` |
| number of remote parameter changes      | `4`   | `0x0004` |
| number of access failures               | `5`   | `0x0005` |
| number of access blocks                 | `6`   | `0x0006` |
| number of real-time clock (RTC) changes | `7`   | `0x0007` |

Command hex dump: `34 0e 00 01 00 02 00 03 00 04 00 05 00 06 00 07`


## See also

* [Access level](../basics.md#command-access-level)
