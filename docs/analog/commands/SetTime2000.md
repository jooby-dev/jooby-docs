# SetTime2000

Time correction command.

It is used when the time difference is more than `127` seconds.
A device should apply it immediately.


## Request

### Format

| Size | Type       | Field                               |
| ---- | ---------- | ----------------------------------- |
| `1`  | `uint8`    | command id = `0x02`                 |
| `1`  | `uint8`    | command size = `5`                  |
| `1`  | `uint8`    | [sequence number](#sequence-number) |
| `4`  | `int32_be` | [seconds](#seconds)                 |

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

| Field           | Value    | Hex          |
| --------------- | -------- | ------------ |
| command id      | `2`      | `0x02`       |
| command size    | `5`      | `0x05`       |
| sequence number | `78`     | `0x4e`       |
| seconds         | `123456` | `0x0001e240` |

Message hex dump with LRC: `02 05 4e 00 01 e2 40 bf`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x02` |
| `1`  | `uint8` | length = `1`        |
| `1`  | `uint8` | [status](#status)   |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **status**

`1` - the time setting was successful <br/>
`0` - time setting failed (the [sequence number](#sequence-number) parameter was not changed)

### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `2`   | `0x02` |
| command size | `1`   | `0x01` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `02 02 01 54`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `2`   | `0x02` |
| command size | `1`   | `0x01` |
| status       | `0`   | `0x00` |

Message hex dump with LRC: `02 02 00 55`


## See also

* [Device time management](../basics.md#device-time-management)
* [Downlink command CorrectTime2000](../commands/CorrectTime2000.md)
* [Uplink event Time2000](../commands/uplink/Time2000.md)
