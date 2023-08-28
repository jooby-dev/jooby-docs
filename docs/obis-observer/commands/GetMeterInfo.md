# GetMeterInfo

Request/response to get the meter profile id and meter address for the specific meter.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x78`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Meter id](../types.md#meter-id)     | meter unique identifier            |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `120` | `0x78` |
| command size | `2`   | `0x02` |
| request id   | `18`  | `0x12` |
| meter id     | `1`   | `0x01` |

Message hex dump: `78 02 01 01`


## Response

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x79`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `4`  | [Meter profile id](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1+` | [String](../types.md#string)                     | meter address                      |


### Examples

| Field            | Value     | Hex                  |
| ---------------- | --------- | -------------------- |
| command id       | `121`     | `0x79`               |
| command size     | `10`      | `0x0a`               |
| request id       | `7`       | `0x07`               |
| meter profile id | `2`       | `0x02`               |
| meter address    | `2345432` | `0x0732333435343332` |

Message hex dump: `79 0a 02 01 07 32 33 34 35 34 33 32`


## See also

* [Request ID](../types.md#request-id)
* [Meter id](../types.md#meter-id)
* [Meter profile id](../types.md#meter-profile-id)
* [String](../types.md#string)