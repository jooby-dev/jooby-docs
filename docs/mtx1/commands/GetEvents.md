# GetEvents

Request/response to get events.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                           |
| ---- | ------- | ----------------------------------------------- |
| `1`  | `uint8` | command id = `0x33`                             |
| `1`  | `uint8` | command size = `4`                              |
| `1`  | `uint8` | year (number of years after `2000`)             |
| `1`  | `uint8` | month (`1` - January ... `12` - December)       |
| `1`  | `uint8` | date (month day number which starts from `1`)   |
| `1`  | `uint8` | offset in the events array of the requested day |

### Examples

| Field                                           | Value | Hex    |
| ----------------------------------------------- | ----- | ------ |
| command id                                      | `51`  | `0x33` |
| command size                                    | `4`   | `0x04` |
| years                                           | `20`  | `0x14` |
| month                                           | `2`   | `0x02` |
| date                                            | `5`   | `0x05` |
| offset in the events array of the requested day | `4`   | `0x04` |

Command hex dump: `33 04 14 2 5 4`


## Response

### Format

| Size  | Type              | Field                                                       |
| ----- | ----------------- | ----------------------------------------------------------- |
| `1`   | `uint8`           | command id = `0x33`                                         |
| `1`   | `uint8`           | command size = `5 + 5*n`, where `n` is the number of events |
| `1`   | `uint8`           | year (number of years after `2000`)                         |
| `1`   | `uint8`           | month (`1` - January ... `12` - December)                   |
| `1`   | `uint8`           | date (month day number which starts from `1`)               |
| `1`   | `uint8`           | total number of events for the requested date               |
| `1`   | `uint8`           | offset in the events array of the requested day             |
| `5*n` | [event](./#event) | array of `n` events (can be empty if `n` = 0)               |

### Parameters

#### Event

| Size | Type    | Field                                                                          |
| ---- | ------- | ------------------------------------------------------------------------------ |
| `1`  | `uint8` | hours                                                                          |
| `1`  | `uint8` | minutes                                                                        |
| `1`  | `uint8` | seconds                                                                        |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                                      |
| `1`  | `uint8` | [mtx1 event id](../../mtx3/events.md)<br>[mtx3 event id](../../mtx3/events.md) |

### Examples

| Field                                           | Value | Hex    |
| ----------------------------------------------- | ----- | ------ |
| command id                                      | `51`  | `0x33` |
| command size                                    | `15`  | `0x0f` |
| years                                           | `20`  | `0x14` |
| month                                           | `2`   | `0x02` |
| date                                            | `5`   | `0x05` |
| total number of events for the requested date   | `2`   | `0x02` |
| offset in the events array of the requested day | `4`   | `0x04` |
| hours                                           | `4`   | `0x04` |
| minutes                                         | `35`  | `0x23` |
| seconds                                         | `10`  | `0x0a` |
| event id                                        | `26`  | `0x1a` |
| hours                                           | `14`  | `0x0e` |
| minutes                                         | `18`  | `0x12` |
| seconds                                         | `45`  | `0x2d` |
| event id                                        | `32`  | `0x20` |

Command hex dump: `33 0f 14 02 05 04 23 0a 1a 0e 12 2d 20`


## See also

* [Access level](../basics.md#command-access-level)
* [Mtx1 events](../events.md)
* [Mtx3 events](../../mtx3/events.md)
