# GetOpParamsExt

Request/response to get device operator extended parameters.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x3f` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `63`  | `0x3f` |
| command size | `0`   | `0x00` |

Message hex dump: `3f 00`


## Response

### Format

| Size | Type    | Field                                                                                                                  |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x3f`                                                                                                    |
| `1`  | `uint8` | command size = `9`                                                                                                     |
| `1`  | `uint8` | timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                              |
| `1`  | `uint8` | [define 1](#define-1)                                                                                                  |
| `1`  | `uint8` | timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds |
| `1`  | `uint8` | timeout for relay activation upon restoration of quality voltage, seconds                                              |
| `5`  | `uint8` | reserved bytes                                                                                                         |

### Parameters

#### Define 1

Bit mask:

| Name                        | Bit | Description                                                      |
| --------------------------- | --- | ---------------------------------------------------------------- |
| `RESET_DAY_MAX_POWER_KEY`   | `0` | allow daily maximum power reset by button                        |
| `RESET_MONTH_MAX_POWER_KEY` | `1` | allow monthly maximum power reset by button                      |
| `BLOCK_KEY_OPTOPORT`        | `2` | `1` - optoport is unlocked by button, `0` - optoport is unlocked |
| `MAGNET_SCREEN_CONST`       | `5` | `1` - constant magnetic influence screen                         |

### Examples

| Field                                                                                                                  | Value | Hex            |
| ---------------------------------------------------------------------------------------------------------------------- | ----- | -------------- |
| command id                                                                                                             | `63`  | `0x3f`         |
| command size                                                                                                           | `9`   | `0x9`          |
| timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                              | `1`   | `0x01`         |
| define 1                                                                                                               | `?`   | `0x00`         |
| timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds | `0`   | `0x00`         |
| timeout for relay activation upon restoration of quality voltage, seconds                                              | `5`   | `0x05`         |
| reserved bytes                                                                                                         | `0`   | `0x0000000000` |

Command hex dump: `3f 09 01 00 00 05 0000000000`


## See also

* [Access level](../basics.md#command-access-level)
