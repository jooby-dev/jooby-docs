# UpdateImageWrite

Request/response to write the block of the new image to the device.
This command is part of update procedure.


## Request

### Format

| Size  | Type                                 | Field                               |
| ----- | ------------------------------------ | ----------------------------------- |
| `1`   | `uint8`                              | command id = `0x30`                 |
| `1`   | `uint8`                              | command size (dynamic, `21+`)       |
| `1`   | [Request ID](../types.md#request-id) | request/response unique  identifier |
| `4`   | `uint32_be`                          | offset to write image block         |
| `16+` | `uint8`                              | [image content](#image-content)     |

### Parameters

#### **image content**

The image content size should be a multiple of `16`.
<br/>
In case there is less data it should be padded with zeros.

### Examples

| Field         | Value                    | Hex                                  |
| ------------- | ------------------------ | ------------------------------------ |
| command id    | `48`                     | `0x30`                               |
| command size  | `21`                     | `0x15`                               |
| request id    | `33`                     | `0x21`                               |
| offset        | `2112`                   | `0x0840`                             |
| image content | `0x00010203040506070809` | `0x00010203040506070809000000000000` |

Message hex dump: `30 15 21 00 00 08 40 00 01 02 03 04 05 06 07 08 09 00 00 00 00 00 00`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x31`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `49`  | `0x31` |
| command size | `1`   | `0x01` |
| request id   | `33`  | `0x21` |

Message hex dump: `2b 01 21`


#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                   |
| ----------- | ----------------------------- |
| `1`         | General failure. Invalid crc. |
| `3`         | Format error.                 |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
*
