# GetBatteryStatus

The command to request status information from the sensor battery.

By default, the battery status is measured once per 24 hours.
The state of the battery physically cannot change dramatically.
Response to the request contains the latest measurement results.
This is enough to monitor the battery condition.


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | extra flag = `0x1f` |
| `1`  | `uint8` | command id = `0x05` |
| `1`  | `uint8` | command size = `0`  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `5`   | `0x05` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 05 00 4f`


## Response

It's a mandatory confirmation to [GetBatteryStatus request](./GetBatteryStatus.md#request).

### Format

| Size | Type     | Field                                                                                               |
| ---- | -------- | --------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | extra flag = `0x1f`                                                                                 |
| `1`  | `uint8`  | command id = `0x05`                                                                                 |
| `1`  | `uint8`  | command size = `11`                                                                                 |
| `2`  | `uint16` | [voltage under low load](#voltage-under-low-load) in `mV`                                           |
| `2`  | `uint16` | [voltage under high load](#voltage-under-high-load) in `mV`                                         |
| `2`  | `uint16` | [internal resistance](#internal-resistance) in `mΩ`                                                 |
| `1`  | `uint8`  | [temperature](#temperature) in degrees Celsius                                                      |
| `1`  | `uint8`  | [remaining capacity](#remaining-capacity) in percents                                               |
| `1`  | `uint8`  | [overconsumption for last 24 hours](#overconsumption-for-last-24-hours)                             |
| `2`  | `uint16` | [counter for exceeding average daily consumption](#counter-for-exceeding-average-daily-consumption) |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### voltage under low load

Voltage under minimum load (sleep mode), value in `mV`. Typical value is about `3600` `mV`.
If the voltage value is `4095` `mV`, then the value is unknown.

#### voltage under high load

Voltage under load simulating transmission mode, value in `mV`. Typical value is about `3600` `mV`.
If the voltage value is `4095` `mV`, then the value is unknown.

#### internal resistance

Internal resistance of the battery in `mΩ`.
If the value of the internal resistance is `65535` `mOhm`, then the resistance is unknown.
Max value is about `60000` `mOhm`. Typical range is about `5000..28000` `mOhm`.

#### temperature

It's a signed number in degrees Celsius.

#### remaining capacity

It's the remaining battery capacity, where `254` is `100%`.
A value of `255` means that the remaining battery capacity is unknown.

#### overconsumption for last 24 hours

Flag is set when consumption over the last 24 hours was higher than estimated.

#### counter for exceeding average daily consumption

Counter for exceeding average daily consumption.

### Examples

| Field                                           | Value  | Hex      |
| ----------------------------------------------- | ------ | -------- |
| extra flag                                      | `31`   | `0x1f`   |
| command id                                      | `5`    | `0x05`   |
| command size                                    | `11`   | `0x0b`   |
| voltage under low load                          | `3600` | `0x100e` |
| voltage under high load                         | `3600` | `0x100e` |
| internal resistance                             | `1034` | `0x0a04` |
| temperature                                     | `15`   | `0x0f`   |
| remaining capacity                              | `41`   | `0x29`   |
| overconsumption for last 24 hours               | `0`    | `0x00`   |
| counter for exceeding average daily consumption | `34`   | `0x2200` |

Message hex dump with LRC: `1f 05 0b 10 0e 10 0e 0a 04 0f 29 00 22 00 4e`
