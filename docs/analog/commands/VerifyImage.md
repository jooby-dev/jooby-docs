# VerifyImage

Command to verify the update image on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type   | Field               |
| ---- | ------ | ------------------- |
| `1`  | `byte` | extra flag = `0x1f` |
| `1`  | `byte` | command id = `0x2b` |
| `1`  | `byte` | command size        |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `43`  | `0x2b` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 2b 00 34`


## Response

### Format

| Size | Type   | Field             |
| ---- | ------ | ----------------- |
| `1`  | `31`   | `0x1f`            |
| `1`  | `43`   | `0x2b`            |
| `1`  | `1`    | `0x01`            |
| `1`  | `byte` | [status](#status) |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **status**

`1` - the image is correct <br>
`0` - the image is incorrect

### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `43`  | `0x2b` |
| command size | `1`   | `0x01` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `1f 2b 01 01 34`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `43`  | `0x2b` |
| command size | `1`   | `0x01` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `1f 2b 01 01 35`
