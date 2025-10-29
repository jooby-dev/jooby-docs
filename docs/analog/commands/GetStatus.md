# GetStatus

The command to request status information from the sensor.


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x14` |
| `1`  | `uint8` | command size = `0`  |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `20`  | `0x14` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `14 00 41`


## Response

It's a mandatory confirmation to [GetStatus request](./GetStatus.md#request).
It is also sent by the sensor without a request once a day.

### Format

| Size | Type     | Field                                                                 |
| ---- | -------- | --------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x14`                                                   |
| `1`  | `uint8`  | command size = `12`                                                   |
| `1`  | `uint8`  | [software type](#software-type) = `2`                                 |
| `1`  | `uint8`  | [software version](#software-version)                                 |
| `1`  | `uint8`  | [hardware type](#hardware-type)                                       |
| `1`  | `uint8`  | [hardware version](#hardware-version)                                 |
| `3`  | `uint8`  | [battery voltage](#battery-voltage) in `mV`                           |
| `2`  | `uint16` | [battery internal resistance](#battery-internal-resistance) in `mΩ`   |
| `1`  | `uint8`  | [temperature](#temperature) in degrees Celsius                        |
| `1`  | `uint8`  | [remaining battery capacity](#remaining-battery-capacity) in percents |
| `1`  | `uint8`  | [sequence number](#sequence-number)                                   |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### software type

Software type which at the moment is always `2`.

#### software version

Software version of the firmware.

#### hardware type

Device type.

#### hardware version

Device type revision.

#### battery voltage

`3` bytes that store battery voltage values under different load.
Under low load - battery voltage under minimum load (sleep mode), value in `mV`. Typical value is about `3600` `mV`.
Under high load - battery voltage under load simulating transmission mode, value in `mV`. Typical value is about `3600` `mV`.
If the voltage value is `4095` `mV`, then the value is unknown.
Voltage values bit map (each line is a byte):

<table>
    <thead>
        <tr>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
            <th>0</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="8" align="center">under low load [<code>11..4</code>]</td>
        </tr>
        <tr>
            <td colspan="4" align="center">under low load [<code>3..0</code>]</td>
            <td colspan="4" align="center">under high load [<code>11..8</code>]</td>
        </tr>
        <tr>
            <td colspan="8" align="center">under high load [<code>7..0</code>]</td>
        </tr>
    </tbody>
</table>

#### battery internal resistance

Internal resistance of the battery in `mΩ`.
If the value of the internal resistance is `65535` `mOhm`, then the resistance is unknown.
Max value is about `60000` `mOhm`. Typical range is about `5000..28000` `mOhm`.

#### temperature

It's a signed number in degrees Celsius.

#### remaining battery capacity

It's the remaining battery capacity, where `254` is `100%`.
A value of `255` means that the remaining battery capacity is unknown.

#### sequence number

The last unread sensor event number in `48` hours.
This field will automatically reset after `48` hours.
After reading the sensor status, this field is also reset.

### Examples

| Field                       | Value                          | Bits                                               | Hex        |
| --------------------------- | ------------------------------ | -------------------------------------------------- | ---------- |
| command id                  | `20`                           |                                                    | `0x14`     |
| command size                | `12`                           |                                                    | `0x0c`     |
| software type               | `2`                            |                                                    | `0x02`     |
| software version            | `10`                           |                                                    | `0x0a`     |
| hardware type               | `GAZI3` = `3`                  |                                                    | `0x03`     |
| hardware version            | `1`                            |                                                    | `0x01`     |
| battery voltage             | low: `3158` <br/> high: `3522` | `0b11000101` <br/> `0b01101101` <br/> `0b11000010` | `0xc56dc2` |
| battery internal resistance | `10034`                        |                                                    | `0x2732`   |
| temperature                 | `14`                           |                                                    | `0x0e`     |
| remaining battery capacity  | `41%` = `104`                  |                                                    | `0x68`     |
| sequence number             | `34`                           |                                                    | `0x22`     |

Message hex dump with LRC: `14 0c 02 0a 03 01 c5 6d c2 27 32 0e 68 22 7c`
