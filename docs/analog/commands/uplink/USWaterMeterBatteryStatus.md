# USWaterMeterBatteryStatus

Command for transmitting the water meter’s battery status (radio module powered by a separate battery).
It is sent every 24 hours.


## Event

### Format

| Size | Type                                                      | Field                                                       |
| ---- | --------------------------------------------------------- | ----------------------------------------------------------- |
| `1`  | `uint8`                                                   | extra flag = `0x1f`                                         |
| `1`  | `uint8`                                                   | command id = `0x14`                                         |
| `1`  | `uint8`                                                   | command size = `7`                                          |
| `7`  | [packed battery data](../../types.md#packed-battery-data) | battery current, internal resistance and depassivation time |

It's a command with a [three-bytes header](../../message.md#command-with-a-three-bytes-header).


### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| extra flag | `31`  | `0x1f` |
| command id | `42`  | `0x07` |


| Field                  | Value              | Bits         | Hex    |
| ---------------------- | ------------------ | ------------ | ------ |
| extra flag             | `31`               |              | `0x1f` |
| command id             | `20`               |              | `0x14` |
| command size           | `7`                |              | `0x07` |
| packed battery data #0 | low + high voltage | `0b11100001` | `0xe1` |
| packed battery data #1 | `3600` `mV`        | `0b00001111` | `0x0f` |
| packed battery data #2 | `3850` `mV`        | `0b00001010` | `0x0a` |
| packed battery data #3 | resistance         | `0b01001000` | `0x48` |
| packed battery data #4 | `18500` `mOhm`     | `0b01000100` | `0x44` |
| packed battery data #5 | depassivation time | `0b00000001` | `0x01` |
| packed battery data #6 | `400` seconds      | `0b10010000` | `0x90` |

Message hex dump with LRC: `1f 14 07 e1 0f 0a 48 44 01 90 20`


## See also

* [Packed battery data](../../types.md#packed-battery-data)
