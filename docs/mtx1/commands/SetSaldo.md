# SetSaldo

Request/response to set the device current saldo information.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                |
| ---- | ------- | -------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x2a`                                                  |
| `1`  | `uint8` | command size `12`                                                    |
| `1`  | `uint8` | current month (`1` - January ... `12` - December)                    |
| `1`  | `uint8` | current date (month day number which starts from `1`)                |
| `1`  | `uint8` | current hour                                                         |
| `1`  | `uint8` | current minute                                                       |
| `1`  | `int32` | new saldo to set                                                     |
| `1`  | `int32` | old saldo (value obtained through [GetSaldo](./GetSaldo.md) command) |

### Examples

| Field        | Value           | Hex          |
| ------------ | --------------- | ------------ |
| command id   | `42`            | `0x2a`       |
| command size | `12`            | `0x0c`       |
| month        | `9` (September) | `0x09`       |
| date         | `23`            | `0x17`       |
| hour         | `6`             | `0x06`       |
| minute       | `35`            | `0x23`       |
| new saldo    | `2`             | `0x00000002` |
| old saldo    | `5`             | `0x00000005` |

Command hex dump: `2a 0c 09 17 06 23 00 00 00 02 00 00 00 05`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x2a` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `42`  | `0x2a` |
| command size | `0`   | `0x00` |

Command hex dump: `2a 00`


## See also

* [Access level](../basics.md#command-access-level)
