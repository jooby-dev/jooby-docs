# SetDemandParameters

Request/response to setup the parameters for voltage graphs and SAIDI.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Field        | Value   | Hex                                                         |
| ------------ | ------- | ----------------------------------------------------------- |
| command id   | `116`   | `0x74`                                                      |
| command size | `4`     | `0x04`                                                      |
| `1`          | `uint8` | [channel param 1](./GetDemandParameters.md#channel-param-1) |
| `1`          | `uint8` | power-off tracking interval, minutes                        |
| `1`          | `uint8` | [channel param 2](./GetDemandParameters.md#channel-param-2) |
| `1`          | `uint8` | reserved byte                                               |

### Examples

| Field                                                       | Value                                   | Hex    |
| ----------------------------------------------------------- | --------------------------------------- | ------ |
| command id                                                  | `116`                                   | `0x74` |
| command size                                                | `4`                                     | `0x04` |
| [channel param 1](./GetDemandParameters.md#channel-param-1) | voltage profile disabled                | `0x00` |
| power-off tracking interval, minutes                        | `20` minutes                            | `0x14` |
| [channel param 2](./GetDemandParameters.md#channel-param-2) | `15/30/60`-minute phase voltage profile | `0xa0` |
| reserved byte                                               | `0`                                     | `0x00` |

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
