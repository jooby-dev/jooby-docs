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
| `4`  | `uint32` | [main mode display settings](#display-settings)                        |
| `4`  | `uint32` | [extended mode display settings](#display-settings)                    |
| `4`  | `uint32` | [battery mode display settings 1](./GetOpParams.md#display-settings-1) |
| `4`  | `uint32` | [battery mode display settings 2](./GetOpParams.md#display-settings-2) |
| `4`  | `uint32` | [battery mode display settings 3](./GetOpParams.md#display-settings-3) |
| `4`  | `uint32` | [battery mode display settings 4](./GetOpParams.md#display-settings-4) |
| `4`  | `uint32` | [battery mode display settings 5](#display-settings)                   |

### Parameters

#### Display-settings

Bit mask:

| Name          | Bit | Description                                            |
| ------------- | --- | ------------------------------------------------------ |
| `EVENT_P98`   | `0` | journal of event profile `P.98`                        |
| `PROFILE_P01` | `1` | journal of load graph profile `1.5.0` `P.01`           |
| `PROFILE_P02` | `2` | journal of load graph profile `2.5.0` `P.02`           |
| `PROFILE_P03` | `3` | journal of load graph profile `3.5.0` (`5.5.0`) `P.03` |
| `PROFILE_P04` | `4` | journal of load graph profile `4.5.0` (`6.5.0`) `P.05` |
| `PROFILE_P05` | `5` | journal of load graph profile `7.5.0` `P.05`           |
| `PROFILE_P06` | `6` | journal of load graph profile `8.5.0` `P.06`           |

### Examples

| Field                                                                  | Value | Hex          |
| ---------------------------------------------------------------------- | ----- | ------------ |
| command id                                                             | `117` | `0x75`       |
| command size                                                           | `28`  | `0x1c`       |
| [main mode display settings](#display-settings)                        | `?`   | `0x0000005b` |
| [extended mode display settings](#display-settings)                    | `?`   | `0x00000055` |
| [battery mode display settings 1](./GetOpParams.md#display-settings-1) | `?`   | `0x40040220` |
| [battery mode display settings 2](./GetOpParams.md#display-settings-2) | `?`   | `0x01000822` |
| [battery mode display settings 3](./GetOpParams.md#display-settings-3) | `?`   | `0x0c001018` |
| [battery mode display settings 4](./GetOpParams.md#display-settings-4) | `?`   | `0x40180018` |
| [battery mode display settings 5](#display-settings)                   | `?`   | `0x0000001c` |

Command hex dump: `75 1c 0000005b 00000055 40040220 01000822 0c001018 40180018 0000001c`


## See also

* [Access level](../basics.md#command-access-level)
