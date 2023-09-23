# RemoveMeterProfile

Request/response to remove the specific meter profile.

## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x62`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |


### Examples

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `98`  | `0x62` |
| command size     | `2`   | `0x02` |
| request id       | `18`  | `0x12` |
| meter profile id | `2`   | `0x02` |

Message hex dump: `62 02 12 02`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x63`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `99`  | `0x63` |
| command size | `1`   | `0x01` |
| request id   | `7`   | `0x07` |

Message hex dump: `63 01 07`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description   |
| ----------- | ------------- |
| `3`         | Format error. |

## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
 