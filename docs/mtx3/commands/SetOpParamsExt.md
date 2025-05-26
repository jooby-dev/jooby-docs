# SetOpParamsExt

Request/response to set device operator parameters.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                                                                                  |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x3f`                                                                                                    |
| `1`  | `uint8` | command size = `9`                                                                                                     |
| `1`  | `uint8` | timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                              |
| `1`  | `uint8` | [define 1](./GetOpParamsExt.md#define-1)                                                                               |
| `1`  | `uint8` | timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds |
| `1`  | `uint8` | timeout for relay activation upon restoration of quality voltage, seconds                                              |
| `5`  | `uint8` | reserved bytes                                                                                                         |

### Examples

| Field                                                                                                                  | Value | Hex            |
| ---------------------------------------------------------------------------------------------------------------------- | ----- | -------------- |
| command id                                                                                                             | `64`  | `0x40`         |
| command size                                                                                                           | `9`   | `0x9`          |
| timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                              | `1`   | `0x01`         |
| define 1                                                                                                               | `?`   | `0x00`         |
| timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds | `0`   | `0x00`         |
| timeout for relay activation upon restoration of quality voltage, seconds                                              | `5`   | `0x05`         |
| reserved bytes                                                                                                         | `0`   | `0x0000000000` |

Command hex dump: `40 09 01 00 00 05 0000000000`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x40` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `31`  | `0x40` |
| command size | `0`   | `0x00` |

Command hex dump: `40 00`


## See also

* [Access level](../basics.md#command-access-level)
