# SetOpParams

Request/response to set device operator parameters.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                                                                                                        |
| ---- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x1f`                                                                                                                                          |
| `1`  | `uint8`  | command size = `95`                                                                                                                                          |
| `1`  | `uint32` | Maximum voltage threshold, mV                                                                                                                                |
| `1`  | `uint32` | Minimum voltage threshold, mV                                                                                                                                |
| `1`  | `uint32` | Maximum current threshold, mA                                                                                                                                |
| `1`  | `uint32` | Maximum active power threshold for tariff `T1`, Watts                                                                                                        |
| `1`  | `uint32` | Maximum active power threshold for tariff `T2`, Watts                                                                                                        |
| `1`  | `uint32` | Maximum active power threshold for tariff `T3`, Watts                                                                                                        |
| `1`  | `uint32` | Maximum active power threshold for tariff `T4`, Watts                                                                                                        |
| `1`  | `uint32` | Maximum reactive power threshold for tariff `T1`, Volt-ampere reactive                                                                                       |
| `1`  | `uint32` | Maximum reactive power threshold for tariff `T2`, Volt-ampere reactive                                                                                       |
| `1`  | `uint32` | Maximum reactive power threshold for tariff `T3`, Volt-ampere reactive                                                                                       |
| `1`  | `uint32` | Maximum reactive power threshold for tariff `T4`, Volt-ampere reactive                                                                                       |
| `1`  | `uint8`  | Power averaging interval, in minutes                                                                                                                         |
| `1`  | `uint8`  | Start date of the monthly billing period                                                                                                                     |
| `1`  | `uint8`  | Display active time                                                                                                                                          |
| `1`  | `uint8`  | Display active time for each screen                                                                                                                          |
| `4`  | `uint32` | [Display settings 1](./GetOpParams.md#display-settings-1)                                                                                                    |
| `4`  | `uint32` | [Display settings 2](./GetOpParams.md#display-settings-2)                                                                                                    |
| `4`  | `uint32` | [Display settings 3](./GetOpParams.md#display-settings-3)                                                                                                    |
| `4`  | `uint32` | [Relay set](./GetOpParams.md#relay-set)                                                                                                                      |
| `1`  | `uint8`  | [Serial ports set](./GetOpParams.md#serial-ports-set)                                                                                                        |
| `1`  | `uint8`  | Integration period for energy profiles `A+`, `A-`, voltage VA , `0`, `30` - `30`, `1`, `3`, `5`, `10`, `15`, `60` minutes (`ten`)                            |
| `1`  | `uint8`  | Voltage averaging interval `0`, `1`, `3`, `5`, `10`, `15`, `30`, `60` minutes to detect voltage quality                                                      |
| `1`  | `uint8`  | Reserved byte                                                                                                                                                |
| `1`  | `uint8`  | Interval for tracking power off events, in minutes                                                                                                           |
| `1`  | `uint8`  | Reserved byte                                                                                                                                                |
| `1`  | `uint8`  | Timeout for relay deactivation due to poor voltage, seconds                                                                                                  |
| `1`  | `unt8`   | Maximum threshold for the frequency of the grid voltage                                                                                                      |
| `1`  | `unt8`   | Minimum threshold for the frequency of the grid voltage                                                                                                      |
| `1`  | `uint8`  | Year of parameters recording                                                                                                                                 |
| `1`  | `uint8`  | Month of parameters recording                                                                                                                                |
| `1`  | `uint8`  | Date of parameters recording                                                                                                                                 |
| `1`  | `uint8`  | The number of digits after the decimal point for displaying energy values (`0x00` - no digits, `0x01` - `1` digit, `0x02` - `2` digits, `0x03` - `3` digits) |
| `2`  | `int16`  | Numerator of the current transformation ratio                                                                                                                |
| `2`  | `int16`  | Denominator of the current transformation ratio                                                                                                              |
| `2`  | `int16`  | Numerator of the voltage transformation ratio                                                                                                                |
| `2`  | `int16`  | Denominator of the voltage transformation ratio                                                                                                              |
| `1`  | `uint8`  | [Measurement type](./GetOpParams.md#measurement-type)                                                                                                        |
| `1`  | `uint16` | Minimum threshold for the `cos φ` value                                                                                                                      |
| `1`  | `uint8`  | Timeout for relay deactivation based on maximum current                                                                                                      |
| `1`  | `uint8`  | Timeout for relay deactivation based on maximum power                                                                                                        |
| `1`  | `uint8`  | Timeout for relay deactivation based on `cos φ`                                                                                                              |
| `1`  | `uint8`  | `PMAX` settings, `0` - `PMAX` = `POWER_A` + `POWER_B` + `POWER_C`; `1` - `PMAX` averaged power over the integration period                                   |
| `4`  | `uint32` | [Display settings 4](./GetOpParams.md#display-settings-4)                                                                                                    |

### Examples

| Field                                                                     | Value    | Hex          |
| ------------------------------------------------------------------------- | -------- | ------------ |
| command id                                                                | `31`     | `0x1f`       |
| command size                                                              | `95`     | `0x5f`       |
| Maximum voltage threshold,mV                                              | `265000` | `0x00040b28` |
| Minimum voltage threshold, mV                                             | `156000` | `0x00026160` |
| Maximum current threshold, mA                                             | `120000` | `0x0001d4c0` |
| Maximum active power threshold for tariff `T1`, Watts                     | `31800`  | `0x00007c38` |
| Maximum active power threshold for tariff `T2`, Watts                     | `31800`  | `0x00007c38` |
| Maximum active power threshold for tariff `T3`, Watts                     | `31800`  | `0x00007c38` |
| Maximum active power threshold for tariff `T4`, Watts                     | `31800`  | `0x00007c38` |
| Maximum reactive power threshold for tariff `T1`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| Maximum reactive power threshold for tariff `T2`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| Maximum reactive power threshold for tariff `T3`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| Maximum reactive power threshold for tariff `T4`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| Power averaging interval, in minutes                                      | `30`     | `0x1e`       |
| Start date of the monthly billing period                                  | `1`      | `0x01`       |
| Display active time                                                       | `127`    | `0x7f`       |
| Display active time for each screen                                       | ``       | `0x7`        |
| Display settings 1                                                        | `?`      | `0x00001085` |
| Display settings 2                                                        | `?`      | `0x00022200` |
| Display settings 3                                                        | `?`      | `0x00000000` |
| Relay set                                                                 | `?`      | `0x00000303` |
| Serial ports set                                                          | `?`      | `0x44`       |
| Integration period for energy profiles `A+`, `A-`, voltage                | `30`     | `0x1e`       |
| Voltage averaging interval to detect voltage quality                      | `30`     | `0x1e`       |
| Interval for tracking power off events, in minutes                        | `3`      | `0x03`       |
| Reserved byte                                                             | `0`      | `0x00`       |
| Timeout for relay deactivation due to poor voltage, seconds               | `5`      | `0x05`       |
| Maximum threshold for the frequency of the grid voltage                   | `55`     | `0x37`       |
| Minimum threshold for the frequency of the grid voltage                   | `45`     | `0x2d`       |
| Year of parameters recording                                              | `0`      | `0x00`       |
| Month of parameters recording                                             | `0`      | `0x00`       |
| Date of parameters recording                                              | `0`      | `0x00`       |
| The number of digits after the decimal point for displaying energy values | `2`      | `0x02`       |
| Numerator of the current transformation ratio                             | `1`      | `0x0001`     |
| Denominator of the current transformation ratio                           | `1`      | `0x0001`     |
| Numerator of the voltage transformation ratio                             | `1`      | `0x0001`     |
| Denominator of the voltage transformation ratio                           | `1`      | `0x0001`     |
| Measurement type                                                          | `0`      | `0x00`       |
| Minimum threshold for the `cos φ` value                                   | `0`      | `0x0000`     |
| Timeout for relay deactivation based on maximum current                   | `5`      | `0x05`       |
| Timeout for relay deactivation based on maximum power                     | `5`      | `0x05`       |
| Timeout for relay deactivation based on `cos φ`                           | `5`      | `0x05`       |
| `PMAX` settings                                                           | `5`      | `0x05`       |
| Display settings 4                                                        | `?`      | `0x80060000` |

Command hex dump: `1f 5f 00040b28 00026160 0001d4c0 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 1e 01 7f 07 00001085 00022200 00000000 00000303 44 1e 1e 03 00 05 37 2d 00 00 00 02 0001 0001 0001 0001 00 0000 05 05 05 01 80060000`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x1f` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `31`  | `0x1f` |
| command size | `0`   | `0x00` |

Command hex dump: `1f 00`


## See also

* [Access level](../basics.md#command-access-level)
