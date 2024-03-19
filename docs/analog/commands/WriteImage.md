# WriteImage

Command to write the block of the new image to the device.
This command is part of update procedure.


## Request

### Format

| Size | Type        | Field                                  |
| ---- | ----------- | -------------------------------------- |
| `1`  | `uint8`     | extra flag = `0x1f`                    |
| `1`  | `uint8`     | command id = `0x2a`                    |
| `1`  | `uint8`     | command size                           |
| `4`  | `uint32_be` | [offset](#offset) to write image block |
| `8+` | `uint8`     | [image content](#image-content)        |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **offset**

The offset at which to write the image content to the device's flash memory.

#### **image content**

The image content size should be a multiple of `8`.
<br>
In case there is less data it should be padded with zeros.

### Examples

| Field         | Value                                | Hex                                  |
| ------------- | ------------------------------------ | ------------------------------------ |
| extra flag    | `31`                                 | `0x1f`                               |
| command id    | `42`                                 | `0x2a`                               |
| command size  | `20`                                 | `0x14`                               |
| offset        | `64`                                 | `0x40`                               |
| image content | `0x000102030405060708090a0b0c0d0e0f` | `0x000102030405060708090a0b0c0d0e0f` |

Message hex dump with LRC: `1f 2a 14 00 00 00 40 00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f 61`


## Response

### Format

| Size | Type        | Field                                  |
| ---- | ----------- | -------------------------------------- |
| `1`  | `31`        | `0x1f`                                 |
| `1`  | `42`        | `0x2a`                                 |
| `4`  | `uint32_be` | [offset](#offset) to write image block |
| `1`  | `uint8`     | [status](#status)                      |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **offset**

The offset at which to write the image content to the device's flash memory.

#### **status**

`1` - the writing was successful <br>
`0` - the writing failed

### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `42`  | `0x2a` |
| command size | `5`   | `0x05` |
| offset       | `64`  | `0x40` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `1f 2a 05 00 00 00 40 01 71`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `42`  | `0x2a` |
| command size | `5`   | `0x05` |
| offset       | `64`  | `0x40` |
| status       | `0`   | `0x00` |

Message hex dump with LRC: `1f 2a 05 00 00 00 40 00 70`
