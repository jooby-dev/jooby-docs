# GetTime2000

The command to request sensor current time.


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x09` |
| `1`  | `uint8` | command size = `9`  |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `9`   | `0x09` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `09 00 5c`


## Response

It's a mandatory confirmation to [GetTime2000 request](./GetTime2000.md#request).
It is sent immediately after device power on.
After it a device sends it periodically (once per 24 hours).

### Format

| Size | Type        | Field                               |
| ---- | ----------- | ----------------------------------- |
| `1`  | `uint8`     | command id = `0x09`                 |
| `1`  | `uint8`     | command size = `5`                  |
| `1`  | `uint8`     | [sequence number](#sequence-number) |
| `4`  | `uint32_be` | [seconds](#seconds)                 |

It's a command with a [two-bytes header](../../message.md#command-with-a-two-bytes-header).

### Parameters

#### **sequence number**

It's the same sequence number last used in a time correction command ([SetTime2000](../SetTime2000.md) or [CorrectTime2000](../CorrectTime2000.md)).

Equals `0` in case it's the first event after the device start.

#### **seconds**

Time in the [time 2000](../../types.md#time-2000) format.

### Examples

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `9`         | `0x09`       |
| command size    | `5`         | `0x05`       |
| sequence number | `77`        | `0x4d`       |
| seconds         | `733845677` | `0x2bbd98ad` |

Message hex dump with LRC: `09 05 4d 2b bd 98 ad b7`


## See also

* [Device time management](../../basics.md#device-time-management)
* [Downlink command SetTime2000](../SetTime2000.md)
* [Downlink command CorrectTime2000](../CorrectTime2000.md)
