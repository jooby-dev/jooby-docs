# SetOpParamsExt2

Request/response to set device operator parameters `2`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                                                                                                          |
| ---- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x1e`                                                                                                                                            |
| `1`  | `uint8`  | command size = `28`                                                                                                                                            |
| `1`  | `uint8`  | Allowed correction interval (`15` minutes by default)                                                                                                          |
| `1`  | `uint8`  | Timeout for relay shutdown upon magnetic interference, seconds                                                                                                 |
| `1`  | `uint8`  | [Relay set](#relay-set)                                                                                                                                        |
| `1`  | `uint8`  | Timeout for relay activation after magnetic field removal, seconds                                                                                             |
| `1`  | `uint8`  | Default PLC Phase.  `0`, `1` - Phase A, `2` - Phase B, `3` - Phase C                                                                                           |
| `4`  | `uint32` | [Display settings 1](./GetOpParams.md#display-settings-1)                                                                                                      |
| `4`  | `uint32` | [Display settings 2](./GetOpParams.md#display-settings-2)                                                                                                      |
| `4`  | `uint32` | [Display settings 3](./GetOpParams.md#display-settings-3)                                                                                                      |
| `4`  | `uint32` | [Display settings 4](./GetOpParams.md#display-settings-4)                                                                                                      |
| `1`  | `uint8`  | [Channel load profile 1. If enabled, it will use half of the A+ archive space](./GetOpParamsExt2.md#channel-load-profile)                                      |
| `1`  | `uint8`  | [Channel load profile 2. If enabled, it will use half of the A+R+ archive space](./GetOpParamsExt2.md#channel-load-profile)                                    |
| `1`  | `uint8`  | [Channel load profile 3. If enabled, it will use half of the A+R- archive space](./GetOpParamsExt2.md#channel-load-profile)                                    |
| `1`  | `uint8`  | [Channel load profile 4. If enabled, it will use half of the A- archive space](./GetOpParamsExt2.md#channel-load-profile)                                      |
| `1`  | `uint8`  | [Channel load profile 5. If enabled, it will use half of the A-R+ archive space](./GetOpParamsExt2.md#channel-load-profile)                                    |
| `1`  | `uint8`  | [Channel load profile 6. If enabled, it will use half of the A-R- archive space](./GetOpParamsExt2.md#channel-load-profile)                                    |
| `1`  | `uint8`  | Allowed correction period, in hours (`24` hours by default). If bit `7` is `0` (default is `0`), time correction crossing the half-hour boundary is forbidden. |


### Examples

| Field                                                               | Value | Hex          |
| ------------------------------------------------------------------- | ----- | ------------ |
| command id                                                          | `69`  | `0x45`       |
| command size                                                        | `28`  | `0x1c`       |
| Allowed correction interval (`15` minutes by default)               | `15`  | `0x0f`       |
| Timeout for relay shutdown upon magnetic interference, seconds      | `5`   | `0x05`       |
| [Relay set](#relay-set)                                             | `5`   | `0x05`       |
| Timeout for relay activation after magnetic field removal, seconds  | `5`   | `0x05`       |
| Default PLC Phase                                                   | `1`   | `0x01`       |
| [Display settings 1](./GetOpParams.md#display-settings-1)           | `?`   | `0x00000000` |
| [Display settings 2](./GetOpParams.md#display-settings-2)           | `?`   | `0x00000000` |
| [Display settings 3](./GetOpParams.md#display-settings-3)           | `?`   | `0x00000000` |
| [Display settings 4](./GetOpParams.md#display-settings-4)           | `?`   | `0x40000000` |
| [Channel load profile 1](./GetOpParamsExt2.md#channel-load-profile) | `1`   | `0x01`       |
| [Channel load profile 2](./GetOpParamsExt2.md#channel-load-profile) | `2`   | `0x02`       |
| [Channel load profile 3](./GetOpParamsExt2.md#channel-load-profile) | `3`   | `0x03`       |
| [Channel load profile 4](./GetOpParamsExt2.md#channel-load-profile) | `4`   | `0x04`       |
| [Channel load profile 5](./GetOpParamsExt2.md#channel-load-profile) | `5`   | `0x05`       |
| [Channel load profile 6](./GetOpParamsExt2.md#channel-load-profile) | `6`   | `0x06`       |
| Allowed correction period, in hours                                 | `?`   | `0x98`       |

Command hex dump: `47 1c 0f 05 05 05 01 00000000 00000000 00000000 04000000 01 02 03 04 05 06 98`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x45` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `69`  | `0x45` |
| command size | `0`   | `0x00` |

Command hex dump: `45 00`


## See also

* [Access level](../basics.md#command-access-level)
