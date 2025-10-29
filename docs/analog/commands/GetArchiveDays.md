# GetArchiveDays

The command for requesting the archive of daily data from the pulse counter sensor.
If there is no data available in the archive, `0xffffffff` will be returned.
Due to the limited length of transmitted data from the sensor, not all requested data will be transferred.


## Request

### Format

| Size | Type                                   | Field                                 |
| ---- | -------------------------------------- | ------------------------------------- |
| `1`  | `uint8`                                | command id = `0x06`                   |
| `1`  | `uint8`                                | command size = `3`                    |
| `2`  | [packed date](../types.md#packed-date) | [start date](#start-date)             |
| `1`  | `uint8`                                | [number of values](#number-of-values) |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### start date

Start date for requested day pulse counter's values.
<br/>
[See details](../types.md#packed-date).

#### number of values

The number or records to receive from archive.

### Examples

| Field            | Value                     | Bits                 | Hex      |
| ---------------- | ------------------------- | -------------------- | -------- |
| command id       | `6`                       |                      | `0x06`   |
| command size     | `6`                       |                      | `0x06`   |
| start date       | `2023.03.10 00:00:00 GMT` | `0b0010111001101010` | `0x2e6a` |
| number of values | `1`                       |                      | `0x01`   |

Message hex dump with LRC: `06 03 2e 6a 01 15`


## Response

The response to the command for requesting the archive of daily data from the pulse counter sensor.

### Format

| Size  | Type                                   | Field                                           |
| ----- | -------------------------------------- | ----------------------------------------------- |
| `1`   | `uint8`                                | command id = `0x06`                             |
| `1`   | `uint8`                                | command size (dynamic, `6+`)                    |
| `2`   | [packed date](../types.md#packed-date) | [start date](#start-date)                       |
| `1*n` | `uint8`                                | [magnet influence flag](#magnet-influence-flag) |
| `3*n` | `uint8`                                | [counter value](#counter-value)                 |

> `n` - the number of day data.

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### start date

Start date for requested day pulse counter's values.
<br/>
[See details](../types.md#packed-date).

#### magnet influence flag

The magnetic influence bit flag indicates that there was a magnet intervention.
The flag set as one highest bit:
<br/>
`0x00` - no magnetic influence
<br/>
`0x80` - magnetic influence is present

#### counter value

It's a pulse counter value packed in `3` bytes.

**Note**

The last two blocks ([magnet influence flag](#magnet-influence-flag) and [counter value](#counter-value)) can be repeated together `n` times.


### Examples

| Field                       | Value        | Bits                 | Hex        |
| --------------------------- | ------------ | -------------------- | ---------- |
| command id                  | `6`          |                      | `0x06`     |
| command size                | `6`          |                      | `0x06`     |
| start date                  | `2001.03.10` | `0b1010100101101101` | `0xa96d`   |
| magnetic influence flag `0` | `true`       | `0b10000000`         | `0x80`     |
| number of values `0`        | `234`        |                      | `0x0000ea` |

Message hex dump with LRC: `06 06 a9 6d 80 00 00 ea fb`


## See also

* [Packed date](../types.md#packed-date)
