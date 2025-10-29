# USWaterMeterCommand

Command to directly access the ultrasonic water meter.


## Request

### Format

| Size | Type    | Field                                 |
| ---- | ------- | ------------------------------------- |
| `1`  | `uint8` | extra flag = `0x1f`                   |
| `1`  | `uint8` | command id = `0x07`                   |
| `1`  | `uint8` | command size `n`                      |
| `n`  | `uint8` | [water frame data](#water-frame-data) |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### water frame data

Data frame intended for transmission to the water meter, excluding the `START`/`STOP` bytes.

Frame [detailed info](../water-frame.md).

### Examples

| Field            | Value                   | Hex        |
| ---------------- | ----------------------- | ---------- |
| extra flag       | `31`                    | `0x1f`     |
| command id       | `07`                    | `0x07`     |
| command size     | `3`                     | `0x03`     |
| water frame data | request for volume data | `0x032102` |

Message hex dump with LRC: `1f 07 03 03 21 02 6e`


## Response

### Format

| Size | Type    | Field                                 |
| ---- | ------- | ------------------------------------- |
| `1`  | `uint8` | extra flag = `0x1f`                   |
| `1`  | `uint8` | command id = `0x07`                   |
| `1`  | `uint8` | command size `n`                      |
| `n`  | `uint8` | [water frame data](#water-frame-data) |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Examples

| Field        | Value                                    | Hex                        |
| ------------ | ---------------------------------------- | -------------------------- |
| extra flag   | `31`                                     | `0x1f`                     |
| command id   | `42`                                     | `0x07`                     |
| command size | `11`                                     | `0x0b`                     |
| status       | volume data (forward: `3`, reverse: `4`) | `0x0B21020000000300000004` |

Message hex dump with LRC: `1f 07 0b 21 02 00 00 00 03 00 00 00 04`


## See also

* [Water frame info](../water-frame.md)
