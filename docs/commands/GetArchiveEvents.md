# GetArchiveEvents

Command to request/receive events from device archive.


## Request

### Format

| Size   | Type        | Field                                  |
| ------ | ----------- | -------------------------------------- |
| `1`    | `byte`      | command id = `0x0b`                    |
| `1`    | `byte`      | command size = `5`                     |
| `4`    | `uint32_be` | [start time](../types.md#time-2000) |
| `1`    | `byte`      | [events](#events)                      |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **start time**

Start time in seconds to read from archive. In [time 2000](../types.md#time-2000) format.

#### **events**

Amount of events to get from archive.

### Examples

#### channels `1`, `3`, `4`:

| Field        | Value                     | Bits                                 | Hex          |
| ------------ | ------------------------- | ------------------------------------ | -----------  |
| command id   | `11`                      |                                      | `0x0b`       |
| command size | `5`                       |                                      | `0x05`       |
| start time   | `2023.04.03 14:01:17 GMT` | `0b00101011101111011001100010101101` | `0x2bbd98ad` |
| events       | `4`                       |                                      | `0x04`       |

Message hex dump with LRC: `0b 05 2b bd 98 ad 04 fc`


## Response

### Format

| Size   | Type        | Field                                         |
| ------ | ----------- | --------------------------------------------- |
| `1`    | `byte`      | command id = `0x0b`                           |
| `1`    | `byte`      | command size = `6+`                           |
| `4`    | `uint32_be` | [event `1` time](../types.md#time-2000)       |
| `1`    | `byte`      | [event `1` id](#event-id)                     |
| `1`    | `byte`      | [event `1` sequence number](#sequence-number) |
| `4`    | `uint32_be` | [event `2` time](../types.md#time-2000)       |
| `1`    | `byte`      | [event `2` id](#event-id)                     |
| `1`    | `byte`      | [event `2` sequence number](#sequence-number) |
| ...    | ...         | ...                                           |
| `4`    | `uint32_be` | [event `N` time](../types.md#time-2000)       |
| `1`    | `byte`      | [event `N` id](#event-id)                     |
| `1`    | `byte`      | [event `N` sequence number](#sequence-number) |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **event `N` time**

Event time in [time 2000](../types.md#time-2000) format.

#### **event id**

One of the [device event](../basics.md#device-events).

#### **sequence number**

It's a unique number for each event.

### Examples

#### 4 events: MAGNET_OFF, MAGNET_ON, ACTIVATE, DEACTIVATE:

| Field                     | Value                     | Bits                                 | Hex          |
| ------------------------- | ------------------------- | ------------------------------------ | ------------ |
| command id                | `11`                      |                                      | `0x0b`       |
| command size              | `24`                      |                                      | `0x18`       |
| event `1` time            | `2023.04.05 13:17:20 GMT` | `0b00101011110000000011000101100000` | `0x2bc03160` |
| event `1` id              | `2`                       |                                      | `0x02`       |
| event `1` sequence number | `1`                       |                                      | `0x01`       |
| event `2` time            | `2023.04.05 16:04:00 GMT` | `0b00101011110000000101100001110000` | `0x2bc05870` |
| event `2` id              | `1`                       |                                      | `0x01`       |
| event `2` sequence number | `2`                       |                                      | `0x02`       |
| event `3` time            | `2023.04.05 18:50:40 GMT` | `0b00101011110000000111111110000000` | `0x2bc07f80` |
| event `3` id              | `3`                       |                                      | `0x03`       |
| event `3` sequence number | `3`                       |                                      | `0x03`       |
| event `4` time            | `2023.04.05 21:37:20 GMT` | `0b00101011110000000011000101100000` | `0x2bc0a690` |
| event `4` id              | `4`                       |                                      | `0x04`       |
| event `4` sequence number | `4`                       |                                      | `0x04`       |

Message hex dump with LRC: `0b 18 2b c0 31 60 02 01 2b c0 58 70 01 02 2b c0 7f 80 03 03 2b c0 a6 90 04 04 f6`


## See also

* [Time 2000](../types.md#time-2000)
* [Device event](../basics.md#device-events).
