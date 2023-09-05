# GetMeterInfo

Request/response to get the meter profile id and meter address for the specific meter.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x78`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |

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

| Size | Type                                             | Mandatory/optional | Field                              |
| ---- | ------------------------------------------------ | ------------------ | ---------------------------------- |
| `1`  | `byte`                                           | mandatory          | command id = `0x79`                |
| `1`  | `byte`                                           | mandatory          | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | mandatory          | request/response unique identifier |
| `1+` | [String](../types.md#string)                     | optional           | meter address                      |
| `4`  | [Meter profile ID](../types.md#meter-profile-id) | optional           | meter profile unique identifier    |


### Examples

| Field            | Value     | Hex                  |
| ---------------- | --------- | -------------------- |
| command id       | `121`     | `0x79`               |
| command size     | `10`      | `0x0a`               |
| request id       | `9`       | `0x09`               |
| meter address    | `2345432` | `0x0732333435343332` |
| meter profile id | `2`       | `0x02`               |


Message hex dump: `79 0a 09 01 07 32 33 34 35 34 33 32 02`


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [String](../types.md#string)