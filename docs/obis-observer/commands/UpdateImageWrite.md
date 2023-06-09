# UpdateImageWrite

Request/response to write the block of the new image to the device.
This command is part of update procedure.


## Request

### Format

| Size | Type                                 | Field                               |
| ---- | ------------------------------------ | ----------------------------------- |
| `1`  | `byte`                               | command id = `0x2a`                 |
| `1`  | `byte`                               | command size (dynamic, `6+`)        |
| `1`  | [Request ID](../types.md#request-id) | request/response unique  identifier |
| `4`  | `uint32_be`                          | offset to write image block         |
| `1+` | `byte`                               | image content                       |

### Examples

| Field         | Value                              | Hex                                |
| ------------- | ---------------------------------- | ---------------------------------- |
| command id    | `42`                               | `0x2a`                             |
| command size  | `21`                               | `0x15`                             |
| request id    | `33`                               | `0x21`                             |
| offset        | `2112`                             | `0x0840`                           |
| image content | `0x000102030405060708090a0b0c0e0f` | `0x000102030405060708090a0b0c0e0f` |

Message hex dump: `2a 15 21 00 00 08 40 00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0e 0f`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x2b`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `43`  | `0x2b` |
| request id  | `33`  | `0x21` |
| result code | `OK`  | `0x00` |

Message hex dump: `2b 21 00`


## See also

* [Request ID](../types.md#request-id)
