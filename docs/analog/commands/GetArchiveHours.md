# GetArchiveHours

Command to request/receive the archive data of hourly consumption.
In the data field of the command, it is necessary to set the start date and hour for reading the archive.
In case there is no data in the archive, a base value of `0xffffffff` will be provided.
Since the length of the transmitted data from the sensor is limited, not all requested data will be transferred.


## Request

### Format

| Size | Type                                   | Field                                 |
| ---- | -------------------------------------- | ------------------------------------- |
| `1`  | `uint8`                                | command id = `0x05`                   |
| `1`  | `uint8`                                | command size = `4`                    |
| `2`  | [packed date](../types.md#packed-date) | [start date](#start-date)             |
| `1`  | `uint8`                                | [start hour](#start-hour)             |
| `1`  | `uint8`                                | [number of values](#number-of-values) |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br>
[See details](../types.md#packed-date).

#### **start hour**

Start hour for requested day pulse counter's values [`0..23`].

#### **number of values**

The number or records to receive from archive.

### Examples

| Field            | Value                     | Bits                 | Hex      |
| ---------------- | ------------------------- | -------------------- | -------- |
| command id       | `5`                       |                      | `0x05`   |
| command size     | `4`                       |                      | `0x04`   |
| start date       | `2023.12.23 00:00:00 GMT` | `0b0010111110010111` | `0x2f97` |
| start hour       | `12:00`                   |                      | `0x0c`   |
| number of values | `2`                       |                      | `0x02`   |

Message hex dump with LRC: `05 04 2f 97 0c 02 e2`


## Response

The response to the command for requesting the archive of hourly data from the pulse counter sensor.

### Format

| Size  | Type                                                                                           | Field                                                                                 |
| ----- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `1`   | `uint8`                                                                                        | command id = `0x05`                                                                   |
| `1`   | `uint8`                                                                                        | command size (dynamic, `8+`)                                                          |
| `2`   | [packed date](../types.md#packed-date)                                                         | [start date](#start-date)                                                             |
| `1`   | [magnetic influence flag and hour](../types.md#packed-magnetic-influence-and-hour)             | [packed info of magnet influence and time](#packed-info-of-magnet-influence-and-time) |
| `3`   | `uint8`                                                                                        | [counter value](#counter-value)                                                       |
| `2*n` | sequence of [magnetic influence flag and diff](../types.md#packed-magnetic-influence-and-diff) | [packed info of magnet influence and diff](#packed-info-of-magnet-influence-and-diff) |

> `n` - the number of hour data diff values.

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **date**

The command contains counter data for this date.
<br>
[See details](../types.md#packed-date).

#### **packed info of magnet influence and time**

The magnetic influence bit flag indicates that there was a magnet intervention during the specified time.
<br>
The command contains counter data for this time.
<br>
[See details](../types.md#packed-magnetic-influence-and-hour).

#### **counter value**

It's a pulse counter value for given date and time packed in `3` bytes.

#### **packed info of magnet influence and diff**

It's a sequence of [magnetic influence flag and diff](../types.md#packed-magnetic-influence-and-diff).
<br>
[See details](../types.md#packed-magnetic-influence-and-diff).

### Examples

| Field                            | Value                         | Bits                 | Hex        |
| -------------------------------- | ----------------------------- | -------------------- | ---------- |
| command id                       | `5`                           |                      | `0x05`     |
| command size                     | `8`                           |                      | `0x08`     |
| date                             | `2023.12.23`                  | `0b0010111110010111` | `0x2f97`   |
| magnetic influence flag and hour | magnet: `true`, time: `12:00` | `0b10001100`         | `0x8c`     |
| counter value                    | `163`                         |                      | `0x0000a3` |
| diff 1                           | magnet: `true`, value: `10`   | `0b1000000000001010` | `0x800a`   |

Message hex dump with LRC: `05 08 2f 97 8c 00 00 a3 80 0a 45`


## See also

* [Packed date](../types.md#packed-date)
* [Magnetic influence flag and hour](../types.md#packed-magnetic-influence-and-hour)
* [Magnetic influence flag and diff](../types.md#packed-magnetic-influence-and-diff)
