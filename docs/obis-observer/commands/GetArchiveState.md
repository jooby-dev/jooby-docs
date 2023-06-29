# GetArchiveState

Request/response to get the archive state, including the record count, eldest record date, and newest record date.


## Request

### Format

| Size | Type                                 | Field                                                                   |
| ---- | ------------------------------------ | ----------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x28`                                                     |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                      |
| `1`  | `byte`                               | archive type: <br> `1` - archive profile 1 <br> `2` - archive profile 2 |

### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `40`  | `0x28` |
| request id | `121` | `0x79` |
| short name | `2`   | `0x02` |

Message hex dump: `28 79 02`


## Response

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x29`                        |
| `1`  | `byte`                               | command size (dynamic, `2+`)               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `4`  | uint32_be                            | count of the archive records               |
| `4`  | [Time 2000](../types.md#time-2000)   | the date of the eldest archive records     |
| `4`  | [Time 2000](../types.md#time-2000)   | the date of the newest archive records     |

### Examples

| Field              | Value                 | Hex          |
| ------------------ | --------------------- | ------------ |
| command id         | `41`                  | `0x29`       |
| command size       | `13`                  | `0x0d`       |
| request id         | `2`                   | `0x02`       |
| records count      | `81`                  | `0x51`       |
| eldest record time | 23-06-27 18:45:02 GMT | `0x2c2deaae` |
| newest record time | 23-06-28 15:15:02 GMT | `0x2c2f0af6` |

Message hex dump: `29 0d 02 00 00 00 51 2c 2d ea ae 2c 2f 0a f6`


## See also

* [Request ID](../types.md#request-id)
* [Time 2000](../types.md#time-2000)
