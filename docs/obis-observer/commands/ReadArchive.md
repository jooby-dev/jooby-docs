# ReadArchive

Request/response to get archive data.


## Request

### Format

| Size | Type                                 | Field                                                                                                                                                                                                                                                      |
| ---- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x11`                                                                                                                                                                                                                                        |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                                                                                                                                                                         |
| `1`  | `byte`                               | archive type: <br> `1` - archive profile 1 <br> `2` - archive profile 2                                                                                                                                                                                    |
| `4`  | [Time 2000](../types.md#time-2000)   | The field specifies a specific time within a day. For example, if the field indicates `14:10`, the response will include all the archived data captured from the start of the nearest archive period to `14:10` until the end of that same archive period. |

### Examples

| Field        | Value                     | Hex          |
| ------------ | ------------------------- | ------------ |
| command id   | `17`                      | `0x11`       |
| request id   | `33`                      | `0x21`       |
| archive type | `Archive profile 1`       | `0x01`       |
| time         | `2023.12.23 00:00:00 GMT` | `0x2d18df80` |

Message hex dump: `11 21 01 2d 18 df 80`


## Response

### Format

| Size | Type                                 | Field                                                                                                            |
| ---- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x12`                                                                                              |
| `1`  | `byte`                               | command size (dynamic, `10+`)                                                                                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                               |
| `4`  | [Time 2000](../types.md#time-2000)   | the date and time at which the data was captured (can be different from the corresponding time field in request) |
| `1`  | [Short name](../types.md#short-name) | short name `1`                                                                                                   |
| `4`  | `float32`                            | OBIS content `1`                                                                                                 |
| ...  | ...                                  | ...                                                                                                              |
| `1`  | [Short name](../types.md#short-name) | short name `N`                                                                                                   |
| `4`  | `float32`                            | OBIS content `N`                                                                                                 |

### Examples

| Field            | Value                     | Hex          |
| ---------------- | ------------------------- | ------------ |
| command id       | `18`                      | `0x12`       |
| command size     | `15`                      | `0x0f`       |
| request id       | `34`                      | `0x22`       |
| time             | `2023.12.23 04:00:00 GMT` | `0x2d1917c0` |
| short name `1`   | `50`                      | `0x32`       |
| OBIS content `1` | `22.27`                   | `0x41b228f6` |
| short name `2`   | `56`                      | `0x38`       |
| OBIS content `2` | `89.33`                   | `0x42b2a8f6` |

Message hex dump: `12 0f 22 2d 19 17 c0 32 41 b2 28 f6 38 42 b2 a8 f6`


## See also

* [Request ID](../types.md#request-id)
* [Time 2000](../types.md#time-2000)
* [Short name](../types.md#short-name)
