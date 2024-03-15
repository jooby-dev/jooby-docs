# CorrectTime2000

Time correction command.

It is used when the time difference is up to `127` seconds.
A device may apply it with a delay.


## Request

### Format

| Size | Type    | Field                               |
| ---- | ------- | ----------------------------------- |
| `1`  | `uint8` | command id = `0x0c`                 |
| `1`  | `uint8` | command size = `2`                  |
| `1`  | `uint8` | [sequence number](#sequence-number) |
| `1`  | `int8`  | [seconds](#seconds)                 |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **sequence number**

It's a unique number for each time correction request.
Use the last received [sequence number](./uplink/Time2000.md#sequence-number) + `1` as a starting point.
Then increment this value for each following request.
It should be done to avoid double processing of the request.

#### **seconds**

The number of seconds to correct device time.
Use positive values to shift time to the future. Negative - to the past.
The new device time will equal the current device time plus the sent value.

### Examples

| Field           | Value  | Hex    |
| --------------- | ------ | ------ |
| command id      | `12`   | `0x0c` |
| command size    | `2`    | `0x02` |
| sequence number | `45`   | `0x2d` |
| seconds         | `-120` | `0x88` |

Message hex dump with LRC: `0c 02 2d 88 fe`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x0c` |
| `1`  | `uint8` | length = `1`        |
| `1`  | `uint8` | [status](#status)   |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **status**

`1` - the time setting was successful <br>
`0` - time setting failed (the [sequence number](#sequence-number) parameter was not changed)

### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `12`  | `0x0c` |
| command size | `1`   | `0x01` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `0c 01 01 59`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `12`  | `0x0c` |
| command size | `1`   | `0x01` |
| status       | `0`   | `0x00` |

Message hex dump with LRC: `0c 01 00 58`


## See also

* [Device time management](../basics.md#device-time-management)
* [Downlink command SetTime2000](../commands/SetTime2000.md)
* [Uplink event Time2000](../commands/uplink/Time2000.md)
