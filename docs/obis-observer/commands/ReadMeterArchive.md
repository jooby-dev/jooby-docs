# ReadMeterArchive

Request/response to get archive data.


## Request

### Format

| Size | Type                                 | Field                                                                                                                                                                                                                                                      |
| ---- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x7f`                                                                                                                                                                                                                                        |
| `1`  | `byte`                               | command size                                                                                                                                                                                                                                               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                                                                                                                                                                         |
| `1`  | `byte`                               | meter unique identifier                                                                                                                                                                                                                                    |
| `1`  | `byte`                               | archive type: <br> `1` - archive 1 <br> `2` - archive 2                                                                                                                                                                                                    |
| `4`  | [Time 2000](../types.md#time-2000)   | The field specifies a specific time within a day. For example, if the field indicates `14:10`, the response will include all the archived data captured from the start of the nearest archive period to `14:10` until the end of that same archive period. |


### Examples

| Field        | Value                     | Hex          |
| ------------ | ------------------------- | ------------ |
| command id   | `127`                     | `0x7f`       |
| command size | `7`                       | `0x07`       |
| request id   | `33`                      | `0x21`       |
| meter id     | `2`                       | `0x02`       |
| archive type | `Archive 1`               | `0x01`       |
| time         | `2023.12.23 00:00:00 GMT` | `0x2d18df80` |

Message hex dump: `7f 07 21 02 01 2d 18 df 80`


## Response

### Format

| Size | Type                                 | Field                                                                                                            |
| ---- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x80`                                                                                              |
| `1`  | `byte`                               | command size (dynamic, `80+`)                                                                                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                               |
| `4`  | [Time 2000](../types.md#time-2000)   | the date and time at which the data was captured (can be different from the corresponding time field in request) |
| `1`  | [OBIS id](../types.md#obis-id)       | OBIS id `1`                                                                                                      |
| `4`  | `float32`                            | OBIS content `1`                                                                                                 |
| ...  | ...                                  | ...                                                                                                              |
| `1`  | [OBIS id](../types.md#obis-od)       | OBIS id `N`                                                                                                      |
| `4`  | `float32`                            | OBIS content `N`                                                                                                 |

### Examples

| Field            | Value                     | Hex          |
| ---------------- | ------------------------- | ------------ |
| command id       | `128`                     | `0x80`       |
| command size     | `15`                      | `0x0f`       |
| request id       | `34`                      | `0x22`       |
| time             | `2023.12.23 04:00:00 GMT` | `0x2d1917c0` |
| OBIS id `1`      | `50`                      | `0x32`       |
| OBIS content `1` | `22.27`                   | `0x41b228f6` |
| OBIS id `2`      | `56`                      | `0x38`       |
| OBIS content `2` | `89.33`                   | `0x42b2a8f6` |

Message hex dump: `80 0f 22 2d 19 17 c0 32 41 b2 28 f6 38 42 b2 a8 f6`


## See also

* [Request ID](../types.md#request-id)
* [Meter id](../types.md#meter-id)
* [Time 2000](../types.md#time-2000)
* [OBIS id](../types.md#obis-id)
