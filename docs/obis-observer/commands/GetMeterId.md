# GetMeterId

Request/response to get the meter id by the meter address.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x76`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1+` | [String](../types.md#string)         | meter address                      |

### Examples

| Field         | Value     | Hex                  |
| ------------- | --------- | -------------------- |
| command id    | `118`     | `0x76`               |
| command size  | `9`       | `0x09`               |
| request id    | `12`      | `0x0c`               |
| meter address | `2345432` | `0x0732333435343332` |

Message hex dump: `76 09 0c 07 32 33 34 35 34 33 32`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x77`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |


### Examples

| Field        | Value | Hex          |
| ------------ | ----- | ------------ |
| command id   | `119` | `0x77`       |
| command size | `5`   | `0x05`       |
| request id   | `12`  | `0x0c`       |
| meter id     | `1`   | `0x00000001` |

Message hex dump: `77 05 0c 00 00 00 01`

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
* [String](../types.md#string)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
