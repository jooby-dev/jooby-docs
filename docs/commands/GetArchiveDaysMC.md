# GetArchiveDaysMC

Command to request/receive day pulse counter's values from device archive.


## Request

### Format

| Size       | Type                                                         | Field                                      |
| ---------- | ------------------------------------------------------------ | ------------------------------------------ |
| `1`        | `byte`                                                       | command id = `0x1b`                        |
| `1`        | `byte`                                                       | command size = `4`                         |
| `2`        | [packed date](../types.md#packed-date)                       | [start date](#date)                        |
| `1..5`     | [extended value](../types.md#extended-value)                 | [channels bit set](#channels-bit-set)      |
| `1`        | `byte`                                                       | [amount of days](#days)                    |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **date**

Start date for requested day pulse counter's values.
<br>
[See details](../../types.md#packed-date).

#### **channels bit set**

[See details](../../types.md#channels-bit-set).

#### **days**

Amount of days from archive.

### Examples

#### channels `1`, `3`, `4`:

| Field        | Value                     | Bits                 | Hex      |
|--------------|---------------------------|----------------------|----------|
| command id   | `27`                      |                      | `0x1b`   |
| command size | `4`                       |                      | `0x04`   |
| date         | `2023.12.23 00:00:00 GMT` | `0b0010111110010111` | `0x2f97` |
| channels     | `1`, `3`, `4`             | `0b00001101`         | `0x0d`   |
| days         | `2`                       |                      | `0x02`   |

Message hex dump with LRC: `1b 04 2f 97 0d 02`


## Response

### Format

| Size         | Type                                                      | Field                                                          |
| ------------ | --------------------------------------------------------- | -------------------------------------------------------------- |
| `1`          | `byte`                                                    | command id = `0x1b`                                            |
| `1`          | `byte`                                                    | command size (dynamic, `5+`)                                   |
| `2`          | [packed date](../types.md#packed-date)                    | [start date](#date)                                            |
| `1..5`       | [extended value](../types.md#extended-value)              | [channels bit set](#channels-bit-set)                          |
| `1`          | `byte`                                                    | [amount of days](#days)                                        |
| `[1..5]*d*n` | sequence of [extended values](../types.md#extended-value) | [sequence of channel values by days ](#channel-values-by-days) |

> `d` - amount of days for each channel. <br>
> `n` - amount of selected channels.

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **date**

Start date for requested day pulse counter's values.
<br>
[See details](../../types.md#packed-date).

#### **channels bit set**

[See details](../types.md#channels-bit-set).

#### **days**

Amount of days from archive.

#### **channel values by days**

It's pulse counter's values by days for each channel.
<br>
[See details](../../types.md#channel-values-by-days).

### Examples

#### single channel `1`:

| Field                     | Value                     | Bits                                                                | Hex      |
|---------------------------|---------------------------|---------------------------------------------------------------------|----------|
| command id                | `27`                      |                                                                     | `0x1b`   |
| command size              | `8`                       |                                                                     | `0x08`   |
| date                      | `2023.12.23 00:00:00 GMT` | `0b0010111110010111`                                                | `0x2f97` |
| channels                  | `1`                       | `0b00000001`                                                        | `0x01`   |
| days                      | `2`                       |                                                                     | `0x02`   |
| channel `1` day `1` value | `234`                     | `0b0000000011101010`<br>with extended bits:<br>`0b1110101000000001` | `0xea01` |
| channel `1` day `2` value | `332`                     | `0b0000000101001100`<br>with extended bits:<br>`0b1100110000000010` | `0xcc02` |

Message hex dump with LRC: `1b 08 a9 6d 01 02 ea 01 cc 02`

#### 4 first channels:

| Field                     | Value                     | Bits                                                                | Hex      |
|---------------------------|---------------------------|---------------------------------------------------------------------|----------|
| command id                | `27`                      |                                                                     | `0x1b`   |
| command size              | `19`                      |                                                                     | `0x13`   |
| date                      | `2023.07.07 00:00:00 GMT` | `0b10111011111011`                                                  | `0x2efb` |
| channels                  | `1`, `2`, `3`, `4`        | `0b00001111`                                                        | `0x0f`   |
| days                      | `2`                       |                                                                     | `0x02`   |
| channel `1` day `1` value | `123`                     | `0b01111011`<br>with extended bits:<br>`0b01111011`                 | `0x7b`   |
| channel `1` day `2` value | `345`                     | `0b0000000101011001`<br>with extended bits:<br>`0b1101100100000010` | `0xd902` |
| channel `2` day `1` value | `455`                     | `0b0000000111000111`<br>with extended bits:<br>`0b0000110001110011` | `0xc703` |
| channel `2` day `2` value | `890`                     | `0b0000001101111010`<br>with extended bits:<br>`0b0000111110100110` | `0xfa06` |
| channel `3` day `1` value | `334`                     | `0b0000000101001110`<br>with extended bits:<br>`0b0000110011100010` | `0xce02` |
| channel `3` day `2` value | `412`                     | `0b0000000110011100`<br>with extended bits:<br>`0b0000100111000011` | `0x9c03` |
| channel `4` day `1` value | `221`                     | `0b0000000011011101`<br>with extended bits:<br>`0b0000110111010001` | `0xdd01` |
| channel `4` day `2` value | `786`                     | `0b0000001100010010`<br>with extended bits:<br>`0b0000100100100110` | `0x9206` |

Message hex dump with LRC: `1b 13 2e fb 0f 02 7b d9 02 c7 03 fa 06 ce 02 9c 03 dd 01 92 06`


## See also

* [Packed date](../types.md#packed-date)
* [Extended value](../types.md#extended-value)
* [Channels bit set](../types.md#channels-bit-set)
* [Channel values by days](../types.md#channel-values-by-days)
