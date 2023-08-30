# GetMeterProfileIdList

Request/response to get the list of the meter profile id.


## Request

### Format

| Size | Type                                 | Field                                   |
| ---- | ------------------------------------ | --------------------------------------- |
| `1`  | `byte`                               | command id = `0x64`                     |
| `1`  | `byte`                               | command size                            |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier      |
| `1`  | `byte`                               | index of the first meter profile to get |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `100` | `0x64` |
| command size | `2`   | `0x02` |
| request id   | `12`  | `0x0c` |
| start index  | `2`   | `0x02` |

Message hex dump: `64 02 0c 02`


## Response

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x65`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | `byte`                                           | number of all meters profiles      |
| `1`  | `byte`                                           | number of ids in message           |
| `1+` | [Meter profile ID](../types.md#meter-profile-id) | meter profile id list              |


### Examples

| Field                         | Value   | Hex      |
| ----------------------------- | ------- | -------- |
| command id                    | `101`   | `0x65`   |
| command size                  | `5`     | `0x05`   |
| request id                    | `12`    | `0x0c`   |
| number of all meters profiles | `4`     | `0x04`   |
| number of ids in message      | `2`     | `0x02`   |
| meter profile id list         | `01 02` | `0x0102` |

Message hex dump: `65 05 0c 04 02 01 02`


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
