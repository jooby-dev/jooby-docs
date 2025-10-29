# GetChannelsTypes

Command to get the types of channels on the device, like IDLE, TEMPERATURE_SENSOR, or BINARY_SENSOR.

## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | extra flag = `0x1f` |
| `1`  | `uint8` | command id = `0x33` |
| `1`  | `uint8` | command size = `0`  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Examples

#### request the status of channels `1` and `2`:

| Field        | Value | Bits | Hex    |
| ------------ | ----- | ---- | ------ |
| extra flag   | `31`  |      | `0x1f` |
| command id   | `51`  |      | `0x33` |
| command size | `0`   |      | `0x00` |

Message hex dump with LRC: `1f 33 00 79`


## Response

It's a response to [GetChannelsTypes request](./GetChannelsTypes.md#request).
The body of the command contains the channel types.

[Channel types](../parameter-types.md#channel-type-values)

### Format

| Size | Type    | Field                                                         |
| ---- | ------- | ------------------------------------------------------------- |
| `1`  | `uint8` | extra flag = `0x1f`                                           |
| `1`  | `uint8` | command id = `0x33`                                           |
| `1`  | `uint8` | command size = `4`                                            |
| `1`  | `uint8` | channel `1` [type](../parameter-types.md#channel-type-values) |
| `1`  | `uint8` | channel `2` [type](../parameter-types.md#channel-type-values) |
| `1`  | `uint8` | channel `3` [type](../parameter-types.md#channel-type-values) |
| `1`  | `uint8` | channel `4` [type](../parameter-types.md#channel-type-values) |

### Examples

| Field            | Value | Hex    | Description        |
| ---------------- | ----- | ------ | ------------------ |
| extra flag       | `31`  | `0x1f` |                    |
| command id       | `51`  | `0x33` |                    |
| command size     | `04`  | `0x04` |                    |
| channel `1` type | `0`   | `0x01` | Power channel      |
| channel `2` type | `0`   | `0x02` | Binary sensor      |
| channel `3` type | `0`   | `0x03` | Temperature sensor |
| channel `4` type | `0`   | `0x00` | Idle channel       |

Message hex dump with LRC: `1f 33 04 01 02 03 00 7d`
