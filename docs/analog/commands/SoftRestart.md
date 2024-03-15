# SoftRestart

Command for software restart.

A device restarts in `~30` seconds with new LoRaWAN parameters.


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x19` |
| `1`  | `uint8` | command size = `0`  |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `25`  | `0x19` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `19 00 4c`


## Response

It's a mandatory confirmation to [SoftRestart request](./SoftRestart.md#request).

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x19` |
| `1`  | `uint8` | length = `0`        |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `25`  | `0x19` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `19 00 4c`
