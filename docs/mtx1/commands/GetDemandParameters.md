# GetDemandParameters

Request/response to get the additional archives information.

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

| Size | Type    | Field                                                                                           |
| ---- | ------- | ----------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x75`                                                                             |
| `1`  | `uint8` | command size = `4`                                                                              |
| `1`  | `uint8` | `10`-minutes voltage archive (`7`-day size)<br>`0` - disable archive<br>`0x40` - enable archive |
| `1`  | `uint8` | time interval for counting power-off events,minutes                                             |
| `1`  | `uint8` | voltage archive (`1`-month size)<br>`0` - disable archive<br>`0xA0` - enable archive            |
| `1`  | `uint8` | reserved byte                                                                                   |

### Examples

| Field                                       | Value              | Hex    |
| ------------------------------------------- | ------------------ | ------ |
| command id                                  | `117`              | `0x75` |
| command size                                | `4`                | `0x04` |
| `10`-minutes voltage archive                | `archive disabled` | `0x00` |
| time interval for counting power-off events | `20`               | `0x14` |
| voltage archive                             | `archive enabled`  | `0xa0` |
| reserved byte                               | `0`                | `0x00` |

Command hex dump: `75 04 00 14 a0 00`


## See also

* [Access level](../basics.md#command-access-level)
