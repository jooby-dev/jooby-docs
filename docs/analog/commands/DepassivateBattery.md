# DepassivateBattery

Command to manually depassivate the device battery.


## Request

### Format

| Size | Type     | Field                                      |
| ---- | -------- | ------------------------------------------ |
| `1`  | `uint8`  | extra flag = `0x1f`                        |
| `1`  | `uint8`  | command id = `0x06`                        |
| `1`  | `uint8`  | command size = `2`                         |
| `2`  | `uint16` | [duration](#duration) in milliseconds      |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### duration

Depassivation duration in milliseconds.

### Examples

| Field        | Value   | Hex      |
| ------------ | ------- | -------- |
| extra flag   | `31`    | `0x1f`   |
| command id   | `6`     | `0x06`   |
| command size | `2`     | `0x02`   |
| duration     | `30000` | `0x7530` |

Message hex dump with LRC: `1f 06 02 75 30 0b`


## Response

It's a mandatory confirmation to [DepassivateBattery request](./DepassivateBattery.md#request).

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | extra flag = `0x1f` |
| `1`  | `uint8` | command id = `0x06` |
| `1`  | `uint8` | command size = `0`  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `6`   | `0x06` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 06 00 4c`
