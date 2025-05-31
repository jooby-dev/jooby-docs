# SetDemandParameters

Request/response to setup the additional archives.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x74` |
| `1`  | `uint8` | command size = `4`  |

### Examples

| Field        | Value   | Hex                                                                                             |
| ------------ | ------- | ----------------------------------------------------------------------------------------------- |
| command id   | `116`   | `0x74`                                                                                          |
| command size | `4`     | `0x04`                                                                                          |
| `1`          | `uint8` | `10`-minutes voltage archive (`7`-day size)<br>`0` - disable archive<br>`0x40` - enable archive |
| `1`          | `uint8` | time interval for counting power-off events,minutes                                             |
| `1`          | `uint8` | voltage archive (`1`-month size)<br>`0` - disable archive<br>`0xA0` - enable archive            |
| `1`          | `uint8` | reserved byte                                                                                   |

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
