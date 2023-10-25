# UpdateRun

Command to run the update on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type   | Field               |
| ---- | ------ | ------------------- |
| `1`  | `byte` | extra flag = `0x1f` |
| `1`  | `byte` | command id = `0x2c` |
| `1`  | `byte` | command size        |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `44`  | `0x2c` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 2c 00 33`


## Response

### Format

| Size | Type   | Field               |
| ---- | ------ | ------------------- |
| `1`  | `byte` | extra flag = `0x1f` |
| `1`  | `byte` | command id = `0x2c` |
| `1`  | `byte` | command size        |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Size         | Type | Field  |
| ------------ | ---- | ------ |
| extra flag   | `31` | `0x1f` |
| command id   | `44` | `0x2c` |
| command size | `0`  | `0x00` |

Message hex dump with LRC: `1f 2c 00 33`
