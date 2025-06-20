# GetDemandParameters

Request/response to get the parameters for voltage graphs and SAIDI.

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

Command hex dump: `75 00`


## Response

### Format

| Size | Type    | Field                                                |
| ---- | ------- | ---------------------------------------------------- |
| `1`  | `uint8` | command id = `0x75`                                  |
| `1`  | `uint8` | command size = `4`                                   |
| `1`  | `uint8` | [channel param 1](#channel-param-1)                  |
| `1`  | `uint8` | time interval for counting power-off events, minutes |
| `1`  | `uint8` | [channel param 2](#channel-param-2)                  |
| `1`  | `uint8` | reserved byte                                        |

### Parameters

#### channel param 1

| Value | Hex    | Description                                                |
| ----- | ------ | ---------------------------------------------------------- |
| `0`   | `0x00` | voltage profile disabled                                   |
| `64`  | `0x40` | `10`-minute phase voltage profile (archive depth `7` days) |

#### channel param 2

| Value | Hex    | Description                                                                                      |
| ----- | ------ | ------------------------------------------------------------------------------------------------ |
| `0`   | `0x00` | voltage profile disabled                                                                         |
| `160` | `0xa0` | `15/30/60`-minute phase voltage profile, determined by parameter `ten` (archive depth `1` month) |

### Examples

| Field                                       | Value                                   | Hex    |
| ------------------------------------------- | --------------------------------------- | ------ |
| command id                                  | `117`                                   | `0x75` |
| command size                                | `4`                                     | `0x04` |
| [channel param 1](#channel-param-1)         | voltage profile disabled                | `0x00` |
| time interval for counting power-off events | `20` minutes                            | `0x14` |
| [channel param 2](#channel-param-2)         | `15/30/60`-minute phase voltage profile | `0xa0` |
| reserved byte                               | `0`                                     | `0x00` |

Command hex dump: `75 04 00 14 a0 00`


## See also

* [Access level](../basics.md#command-access-level)
