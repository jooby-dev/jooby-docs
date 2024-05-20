# GetCorrectTime

Request/response to get [DST](https://en.wikipedia.org/wiki/Daylight_saving_time)/Standard time transition options.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x3e` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `62`  | `0x3e` |
| command size | `0`   | `0x00` |

Message hex dump: `3e 00`


## Response

### Format

| Size | Type    | Field                                                                                           |
| ---- | ------- | ----------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x3e`                                                                             |
| `1`  | `uint8` | command size = `9`                                                                              |
| `1`  | `uint8` | month of transition to `DST`                                                                    |
| `1`  | `uint8` | date of transition to `DST` <br/> if `0` then it refers to the last Sunday of the month         |
| `1`  | `uint8` | hour of transition to `DST`                                                                     |
| `1`  | `uint8` | adjustment in hours during the transition to `DST`                                              |
| `1`  | `uint8` | month of transition to standard time                                                            |
| `1`  | `uint8` | date of transition to standard time <br/> if `0` then it refers to the last Sunday of the month |
| `1`  | `uint8` | hour of transition to standard time                                                             |
| `1`  | `uint8` | adjustment in hours during the transition to standard time                                      |
| `1`  | `uint8` | flag if `DST`/Standard transition is required                                                   |

### Examples

Default parameters:

| Field                                        | Value  | Hex    |
| -------------------------------------------- | ------ | ------ |
| command id                                   | `62`   | `0x3e` |
| command size                                 | `9`    | `0x09` |
| month transition to `DST`                    | `3`    | `0x03` |
| date transition to `DST`                     | `0`    | `0x00` |
| hours transition to `DST`                    | `3`    | `0x03` |
| hours to correct on `DST` transition         | `1`    | `0x01` |
| month transition to standard time            | `10`   | `0x0a` |
| date transition to standard time             | `0`    | `0x00` |
| hours transition to standard time            | `4`    | `0x04` |
| hours to correct on standard time transition | `1`    | `0x01` |
| is correction needed                         | `true` | `0x01` |

Message hex dump: `3e 09 03 00 03 01 0a 00 04 01 01`


## See also

* [Access level](../basics.md#command-access-level)
