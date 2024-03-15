# GetMetersIdList

Request/response to get the list of meters id.


## Request

### Format

| Size | Type                                 | Field                                                |
| ---- | ------------------------------------ | ---------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x74`                                  |
| `1`  | `uint8`                              | command size                                         |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                   |
| `1`  | `uint8`                              | the index of the meter to start forming the response |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `116` | `0x74` |
| command size | `2`   | `0x02` |
| request id   | `12`  | `0x0c` |
| index        | `2`   | `0x02` |

Message hex dump: `74 02 0c 02`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x75`                |
| `1`  | `uint8`                              | command size (dynamic, `2+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `uint8`                              | is list completed                  |
| `1+` | [Meter ID](../types.md#meter-id)     | meter id list                      |


### Examples

| Field             | Value   | Hex      |
| ----------------- | ------- | -------- |
| command id        | `117`   | `0x75`   |
| command size      | `3`     | `0x04`   |
| request id        | `12`    | `0x0c`   |
| is list completed | `1`     | `0x01`   |
| meter id list     | `01 02` | `0x0102` |

Message hex dump: `75 04 0c 01 01 02`


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
