# GetCurrent

Command to request the current pulse counter readings from the sensor.


## Request

### Format

| Size | Type   | Field               |
| ---- | ------ | ------------------- |
| `1`  | `byte` | command id = `0x07` |
| `1`  | `byte` | command size = `0`  |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `7`   | `0x07` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `07 00 52`


## Response

It's a response to [GetCurrent request](./GetCurrent.md#request) for requesting the current pulse counter readings from the sensor.
This command can also be periodically sent by the sensor without a request, if the parameter `5` is set to a value of `2` - transmission of current data.
The body of the command contains the current value of the pulse counter.

### Format

| Size | Type   | Field                                           |
| ---- | ------ | ----------------------------------------------- |
| `1`  | `byte` | command id = `0x07`                             |
| `1`  | `byte` | command size = `4`                              |
| `1`  | `byte` | [magnet influence flag](#magnet-influence-flag) |
| `3`  | `byte` | [counter value](#counter-value)                 |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **magnet influence flag**

The magnetic influence bit flag indicates that there was a magnet intervention.
The flag set as one highest bit:
<br>
`0x00` - no magnetic influence
<br>
`0x80` - magnetic influence is present

#### **counter value**

It's a pulse counter value packed in `3` bytes.

### Examples

| Field                   | Value  | Bits         | Hex        |
| ----------------------- | ------ | ------------ | ---------- |
| command id              | `7`    |              | `0x07`     |
| command size            | `4`    |              | `0x04`     |
| magnetic influence flag | `true` | `0b10000000` | `0x80`     |
| counter value           | `342`  |              | `0x000156` |

Message hex dump with LRC: `07 04 80 00 01 56 81`
