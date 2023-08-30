# GetMetersIdList

Request/response to get the list of meters id.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x74`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | index of the first meter to get    |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `116` | `0x74` |
| command size | `2`   | `0x02` |
| request id   | `12`  | `0x0c` |
| start index  | `2`   | `0x02` |

Message hex dump: `74 02 0c 02`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x75`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | number of all meters               |
| `1`  | `byte`                               | number of ids in message           |
| `1+` | [Meter ID](../types.md#meter-id)     | meter id list                      |


### Examples

| Field                    | Value   | Hex      |
| ------------------------ | ------- | -------- |
| command id               | `117`   | `0x75`   |
| command size             | `5`     | `0x05`   |
| request id               | `12`    | `0x0c`   |
| number of all meters     | `4`     | `0x04`   |
| number of ids in message | `2`     | `0x02`   |
| meter id list            | `01 02` | `0x0102` |

Message hex dump: `75 05 0c 04 02 01 02`


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
