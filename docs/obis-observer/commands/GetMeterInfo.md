# GetMeterInfo

Request/response to get the meter profile id and meter address for the specific meter.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x78`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |

### Examples

| Field        | Value | Hex          |
| ------------ | ----- | ------------ |
| command id   | `120` | `0x78`       |
| command size | `5`   | `0x05`       |
| request id   | `18`  | `0x12`       |
| meter id     | `1`   | `0x00000001` |

Message hex dump: `78 05 12 00 00 00 01`


## Response

### Format

| Size | Type                                             | Mandatory/optional | Field                              |
| ---- | ------------------------------------------------ | ------------------ | ---------------------------------- |
| `1`  | `uint8`                                          | mandatory          | command id = `0x79`                |
| `1`  | `uint8`                                          | mandatory          | command size (dynamic, `1+`)       |
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

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description          |
| ----------- | -------------------- |
| `3`         | Format error.        |
| `9`         | The meter not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [String](../types.md#string)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
