# SetOpParamsExt4

Request/response to set device operator parameters `4`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                    |
| ---- | -------- | ------------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x74`                                                      |
| `1`  | `uint8`  | command size = `28`                                                      |
| `4`  | `uint32` | [Main mode display settings](./GetOpParamsExt4.md#display-settings)      |
| `4`  | `uint32` | [Extended mode display settings](./GetOpParamsExt4.md#display-settings)  |
| `4`  | `uint32` | [Battery mode display settings 1](./GetOpParams.md#display-settings-1)   |
| `4`  | `uint32` | [Battery mode display settings 2](./GetOpParams.md#display-settings-2)   |
| `4`  | `uint32` | [Battery mode display settings 3](./GetOpParams.md#display-settings-3)   |
| `4`  | `uint32` | [Battery mode display settings 4](./GetOpParams.md#display-settings-4)   |
| `4`  | `uint32` | [Battery mode display settings 5](./GetOpParamsExt4.md#display-settings) |

### Examples

| Field                                                                    | Value | Hex          |
| ------------------------------------------------------------------------ | ----- | ------------ |
| command id                                                               | `116` | `0x74`       |
| command size                                                             | `28`  | `0x1c`       |
| [Main mode display settings](./GetOpParamsExt4.md#display-settings)      | `?`   | `0x0000005b` |
| [Extended mode display settings](./GetOpParamsExt4.md#display-settings)  | `?`   | `0x00000055` |
| [Battery mode display settings 1](./GetOpParams.md#display-settings-1)   | `?`   | `0x40040220` |
| [Battery mode display settings 2](./GetOpParams.md#display-settings-2)   | `?`   | `0x01000822` |
| [Battery mode display settings 3](./GetOpParams.md#display-settings-3)   | `?`   | `0x0c001018` |
| [Battery mode display settings 4](./GetOpParams.md#display-settings-4)   | `?`   | `0x40180018` |
| [Battery mode display settings 5](./GetOpParamsExt4.md#display-settings) | `?`   | `0x0000001c` |

Command hex dump: `74 1c 0000005b 00000055 40040220 01000822 0c001018 40180018 0000001c`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x74` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `116` | `0x74` |
| command size | `0`   | `0x00` |

Command hex dump: `75 00`


## See also

* [Access level](../basics.md#command-access-level)
