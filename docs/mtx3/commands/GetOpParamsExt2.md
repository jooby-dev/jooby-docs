# GetOpParamsExt2

Request/response to get device operator extended parameters `2`.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x47` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `71`  | `0x47` |
| command size | `0`   | `0x00` |

Message hex dump: `47 00`


## Response

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
| `1`  | `uint8`  | [Channel load profile 1](#channel-load-profile) (if enabled, it will use half of the A+ archive space)                                                         |
| `1`  | `uint8`  | [Channel load profile 2](#channel-load-profile) (if enabled, it will use half of the A+R+ archive space)                                                       |
| `1`  | `uint8`  | [Channel load profile 3](#channel-load-profile) (if enabled, it will use half of the A+R- archive space)                                                       |
| `1`  | `uint8`  | [Channel load profile 4](#channel-load-profile) (if enabled, it will use half of the A- archive space)                                                         |
| `1`  | `uint8`  | [Channel load profile 5](#channel-load-profile) (if enabled, it will use half of the A-R+ archive space)                                                       |
| `1`  | `uint8`  | [Channel load profile 6](#channel-load-profile) (if enabled, it will use half of the A-R- archive space)                                                       |
| `1`  | `uint8`  | Allowed correction period, in hours (`24` hours by default). If bit `7` is `0` (default is `0`), time correction crossing the half-hour boundary is forbidden. |

### Parameters

#### Relay set

Bit mask:

| Name                      | Bit | Description                                            |
| ------------------------- | --- | ------------------------------------------------------ |
| `RELAY_OFF_MAGNET`        | `0` | Disable relay upon detection of magnetic field         |
| `RELAY_ON_MAGNET_TIMEOUT` | `1` | Enable relay after `timeoutRelayOn` timeout (not used) |
| `RELAY_ON_MAGNET_AUTO`    | `2` | Enable relay after removal of magnetic field           |

#### Channel load profile

| Value | Channel load profile, current, voltage or other                  |
| ----- | ---------------------------------------------------------------- |
| `0`   | Do not archive additional measurement                            |
| `1`   | `1/3/5/10/15/30/60` minutes measurement of the `A+` Phase `A`    |
| `2`   | `1/3/5/10/15/30/60` minutes measurement of the `A+` Phase `B`    |
| `3`   | `1/3/5/10/15/30/60` minutes measurement of the `A+` Phase `C`    |
| `4`   | `1/3/5/10/15/30/60` minutes measurement of the `A-` Phase `A`    |
| `5`   | `1/3/5/10/15/30/60` minutes measurement of the `A-` Phase `B`    |
| `6`   | `1/3/5/10/15/30/60` minutes measurement of the `A-` Phase `C`    |
| `7`   | `1/3/5/10/15/30/60` minutes measurement of the `A+R+` Phase `A`  |
| `8`   | `1/3/5/10/15/30/60` minutes measurement of the `A+R+` Phase `B`  |
| `9`   | `1/3/5/10/15/30/60` minutes measurement of the `A+R+` Phase `C`  |
| `10`  | `1/3/5/10/15/30/60` minutes measurement of the `A+R-` Phase `A`  |
| `11`  | `1/3/5/10/15/30/60` minutes measurement of the `A+R-` Phase `B`  |
| `12`  | `1/3/5/10/15/30/60` minutes measurement of the `A+R-` Phase `C`  |
| `13`  | `1/3/5/10/15/30/60` minutes measurement of the `A-R+` Phase `A`  |
| `14`  | `1/3/5/10/15/30/60` minutes measurement of the `A-R+` Phase `B`  |
| `15`  | `1/3/5/10/15/30/60` minutes measurement of the `A-R+` Phase `C`  |
| `16`  | `1/3/5/10/15/30/60` minutes measurement of the `A-R-` Phase `A`  |
| `17`  | `1/3/5/10/15/30/60` minutes measurement of the `A-R-` Phase `B`  |
| `18`  | `1/3/5/10/15/30/60` minutes measurement of the `A-R-` Phase `C`  |
| `19`  | `1/3/5/10/15/30/60` minutes measurement of the `R+` Phase `A`    |
| `20`  | `1/3/5/10/15/30/60` minutes measurement of the `R+` Phase `B`    |
| `21`  | `1/3/5/10/15/30/60` minutes measurement of the `R+` Phase `C`    |
| `22`  | `1/3/5/10/15/30/60` minutes measurement of the `R-` Phase `A`    |
| `23`  | `1/3/5/10/15/30/60` minutes measurement of the `R-` Phase `B`    |
| `24`  | `1/3/5/10/15/30/60` minutes measurement of the `R-` Phase `C`    |
| `25`  | `1/3/5/10/15/30/60` minutes measurement of the voltage Phase `A` |
| `26`  | `1/3/5/10/15/30/60` minutes measurement of the voltage Phase `B` |
| `27`  | `1/3/5/10/15/30/60` minutes measurement of the voltage Phase `C` |
| `28`  | `10`minute voltage profile Phase `A`                             |
| `29`  | `10`minute voltage profile Phase `B`                             |
| `30`  | `10`minute voltage profile Phase `C`                             |
| `31`  | `1/3/5/10/15/30/60`minute current profile Phase `A`              |
| `32`  | `1/3/5/10/15/30/60`minute current profile Phase `B`              |
| `33`  | `1/3/5/10/15/30/60`minute current profile Phase `C`              |

### Examples

| Field                                                              | Value | Hex          |
| ------------------------------------------------------------------ | ----- | ------------ |
| command id                                                         | `71`  | `0x47`       |
| command size                                                       | `28`  | `0x1c`       |
| Allowed correction interval (`15` minutes by default)              | `15`  | `0x0f`       |
| Timeout for relay shutdown upon magnetic interference, seconds     | `5`   | `0x05`       |
| [Relay set](#relay-set)                                            | `5`   | `0x05`       |
| Timeout for relay activation after magnetic field removal, seconds | `5`   | `0x05`       |
| Default PLC Phase                                                  | `1`   | `0x01`       |
| [Display settings 1](./GetOpParams.md#display-settings-1)          | `?`   | `0x00000000` |
| [Display settings 2](./GetOpParams.md#display-settings-2)          | `?`   | `0x00000000` |
| [Display settings 3](./GetOpParams.md#display-settings-3)          | `?`   | `0x00000000` |
| [Display settings 4](./GetOpParams.md#display-settings-4)          | `?`   | `0x40000000` |
| [Channel load profile 1](#channel-load-profile)                    | `1`   | `0x01`       |
| [Channel load profile 2](#channel-load-profile)                    | `2`   | `0x02`       |
| [Channel load profile 3](#channel-load-profile)                    | `3`   | `0x03`       |
| [Channel load profile 4](#channel-load-profile)                    | `4`   | `0x04`       |
| [Channel load profile 5](#channel-load-profile)                    | `5`   | `0x05`       |
| [Channel load profile 6](#channel-load-profile)                    | `6`   | `0x06`       |
| Allowed correction period, in hours                                | `?`   | `0x98`       |

Command hex dump: `47 1c 0f 05 05 05 01 00000000 00000000 00000000 04000000 01 02 03 04 05 06 98`


## See also

* [Access level](../basics.md#command-access-level)
