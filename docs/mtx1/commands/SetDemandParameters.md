# SetDemandParameters

Request/response to setup the additional archives.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Field        | Value   | Hex                                                             |
| ------------ | ------- | --------------------------------------------------------------- |
| command id   | `116`   | `0x74`                                                          |
| command size | `4`     | `0x04`                                                          |
| `1`          | `uint8` | [archive channel 2](./GetDemandParameters.md#archive-channel-2) |
| `1`          | `uint8` | time interval for counting power-off events,minutes             |
| `1`          | `uint8` | [archive channel 1](./GetDemandParameters.md#archive-channel-1) |
| `1`          | `uint8` | reserved byte                                                   |

### Examples

| Field                                                            | Value                                              | Hex    |
| ---------------------------------------------------------------- | -------------------------------------------------- | ------ |
| command id                                                       | `117`                                              | `0x75` |
| command size                                                     | `4`                                                | `0x04` |
| [archive channel 2](./GetDemandParameters.md##archive-channel-2) | `10`-minute voltage archive disabled               | `0x00` |
| time interval for counting power-off events                      | `20`                                               | `0x14` |
| [archive channel 1](./GetDemandParameters.md##archive-channel-1) | `1/3/5/10/15/30/60`-minute voltage archive enabled | `0xa0` |
| reserved byte                                                    | `0`                                                | `0x00` |

Command hex dump: `74 04 00 14 a0 00`


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

Command hex dump: `74 00`


## See also

* [Access level](../basics.md#command-access-level)
