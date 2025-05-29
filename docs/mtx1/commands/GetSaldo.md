# GetSaldo

Request/response to get device current saldo information.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x29` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `41`  | `0x29` |
| command size | `0`   | `0x00` |

Command hex dump: `29 00`


## Response

### Format

| Size | Type    | Field                                                                    |
| ---- | ------- | ------------------------------------------------------------------------ |
| `1`  | `uint8` | command id = `0x29`                                                      |
| `1`  | `uint8` | command size = `29`                                                      |
| `1`  | `int32` | current saldo                                                            |
| `1`  | `uint8` | counter for saldo installations                                          |
| `4`  | `int32` | energy for tariffs `1`-`4` at the moment of setting a new saldo          |
| `1`  | `int32` | current saldo after setting the saldo                                    |
| `1`  | `uint8` | month of the last saldo installation (`1` - January ... `12` - December) |
| `1`  | `uint8` | date of the last saldo installation                                      |
| `1`  | `uint8` | hour of the last saldo installation                                      |
| `1`  | `uint8` | minute of the last saldo installation                                    |

### Examples

| Field               | Value               | Hex                                  |
| ------------------- | ------------------- | ------------------------------------ |
| command id          | `41`                | `0x29`                               |
| command size        | `29`                | `0x1d`                               |
| current saldo       | `1`                 | `0x00000001`                         |
| counter             | `8`                 | `0x08`                               |
| energy for tariffs  | `2`, `3`,  `4`, `5` | `0x00000002000000030000000400000005` |
| saldo after setting | `7`                 | `0x00000007`                         |
| month               | `9` (September)     | `0x09`                               |
| date                | `23`                | `0x17`                               |
| hour                | `6`                 | `0x06`                               |
| minute              | `35`                | `0x23`                               |

Command hex dump: `29 1d 00 00 00 01 08 00 00 00 02 00 00 00 03 00 00 00 04 00 00 00 05 00 00 00 07 09 17 06 23`


## See also

* [Access level](../basics.md#command-access-level)
