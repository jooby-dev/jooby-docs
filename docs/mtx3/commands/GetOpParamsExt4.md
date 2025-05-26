# GetOpParamsExt4

Request/response to get device operator extended parameters `4`.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x75` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `117` | `0x75` |
| command size | `0`   | `0x00` |

Message hex dump: `75 00`


## Response

### Format

| Size | Type     | Field                                                                  |
| ---- | -------- | ---------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x75`                                                    |
| `1`  | `uint8`  | command size = `28`                                                    |
| `4`  | `uint32` | [Main mode display settings](#display-settings)                        |
| `4`  | `uint32` | [Extended mode display settings](#display-settings)                    |
| `4`  | `uint32` | [Battery mode display settings 1](./GetOpParams.md#display-settings-1) |
| `4`  | `uint32` | [Battery mode display settings 2](./GetOpParams.md#display-settings-2) |
| `4`  | `uint32` | [Battery mode display settings 3](./GetOpParams.md#display-settings-3) |
| `4`  | `uint32` | [Battery mode display settings 4](./GetOpParams.md#display-settings-4) |
| `4`  | `uint32` | [Battery mode display settings 5](#display-settings)                   |

### Parameters

#### Display-settings

Bit mask:

| Name          | Bit | Description                                            |
| ------------- | --- | ------------------------------------------------------ |
| `EVENT_P98`   | `0` | Journal of event profile `P.98`                        |
| `PROFILE_P01` | `1` | Journal of load graph profile `1.5.0` `P.01`           |
| `PROFILE_P02` | `2` | Journal of load graph profile `2.5.0` `P.02`           |
| `PROFILE_P03` | `3` | Journal of load graph profile `3.5.0` (`5.5.0`) `P.03` |
| `PROFILE_P04` | `4` | Journal of load graph profile `4.5.0` (`6.5.0`) `P.05` |
| `PROFILE_P05` | `5` | Journal of load graph profile `7.5.0` `P.05`           |
| `PROFILE_P06` | `6` | Journal of load graph profile `8.5.0` `P.06`           |

### Examples

| Field                                                                  | Value | Hex          |
| ---------------------------------------------------------------------- | ----- | ------------ |
| command id                                                             | `117` | `0x75`       |
| command size                                                           | `28`  | `0x1c`       |
| [Main mode display settings](#display-settings)                        | `?`   | `0x0000005b` |
| [Extended mode display settings](#display-settings)                    | `?`   | `0x00000055` |
| [Battery mode display settings 1](./GetOpParams.md#display-settings-1) | `?`   | `0x40040220` |
| [Battery mode display settings 2](./GetOpParams.md#display-settings-2) | `?`   | `0x01000822` |
| [Battery mode display settings 3](./GetOpParams.md#display-settings-3) | `?`   | `0x0c001018` |
| [Battery mode display settings 4](./GetOpParams.md#display-settings-4) | `?`   | `0x40180018` |
| [Battery mode display settings 5](#display-settings)                   | `?`   | `0x0000001c` |

Command hex dump: `75 1c 0000005b 00000055 40040220 01000822 0c001018 40180018 0000001c`


## See also

* [Access level](../basics.md#command-access-level)
