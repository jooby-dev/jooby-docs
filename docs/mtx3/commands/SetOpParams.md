# SetOpParams

Request/response to set device operator parameters.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                                                                                                        |
| ---- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x1f`                                                                                                                                          |
| `1`  | `uint8`  | command size = `95`                                                                                                                                          |
| `1`  | `uint32` | maximum voltage threshold, mV                                                                                                                                |
| `1`  | `uint32` | minimum voltage threshold, mV                                                                                                                                |
| `1`  | `uint32` | maximum current threshold, mA                                                                                                                                |
| `1`  | `uint32` | maximum active power threshold for tariff `T1`, Watts                                                                                                        |
| `1`  | `uint32` | maximum active power threshold for tariff `T2`, Watts                                                                                                        |
| `1`  | `uint32` | maximum active power threshold for tariff `T3`, Watts                                                                                                        |
| `1`  | `uint32` | maximum active power threshold for tariff `T4`, Watts                                                                                                        |
| `1`  | `uint32` | maximum reactive power threshold for tariff `T1`, Volt-ampere reactive                                                                                       |
| `1`  | `uint32` | maximum reactive power threshold for tariff `T2`, Volt-ampere reactive                                                                                       |
| `1`  | `uint32` | maximum reactive power threshold for tariff `T3`, Volt-ampere reactive                                                                                       |
| `1`  | `uint32` | maximum reactive power threshold for tariff `T4`, Volt-ampere reactive                                                                                       |
| `1`  | `uint8`  | power averaging interval, in minutes                                                                                                                         |
| `1`  | `uint8`  | start date of the monthly billing period                                                                                                                     |
| `1`  | `uint8`  | display active time                                                                                                                                          |
| `1`  | `uint8`  | display active time for each screen                                                                                                                          |
| `4`  | `uint32` | [display settings 1](./GetOpParams.md#display-settings-1)                                                                                                    |
| `4`  | `uint32` | [display settings 2](./GetOpParams.md#display-settings-2)                                                                                                    |
| `4`  | `uint32` | [display settings 3](./GetOpParams.md#display-settings-3)                                                                                                    |
| `4`  | `uint32` | [relay set](./GetOpParams.md#relay-set)                                                                                                                      |
| `1`  | `uint8`  | [serial ports set](./GetOpParams.md#serial-ports-set)                                                                                                        |
| `1`  | `uint8`  | integration period for energy profiles `A+`, `A-`, voltage VA , `0`, `30` - `30`, `1`, `3`, `5`, `10`, `15`, `60` minutes (`ten`)                            |
| `1`  | `uint8`  | voltage averaging interval `0`, `1`, `3`, `5`, `10`, `15`, `30`, `60` minutes to detect voltage quality                                                      |
| `1`  | `uint8`  | reserved byte                                                                                                                                                |
| `1`  | `uint8`  | interval for tracking power off events, in minutes                                                                                                           |
| `1`  | `uint8`  | reserved byte                                                                                                                                                |
| `1`  | `uint8`  | timeout for relay deactivation due to poor voltage, seconds                                                                                                  |
| `1`  | `unt8`   | maximum threshold for the frequency of the grid voltage                                                                                                      |
| `1`  | `unt8`   | minimum threshold for the frequency of the grid voltage                                                                                                      |
| `1`  | `uint8`  | year of parameters recording                                                                                                                                 |
| `1`  | `uint8`  | month of parameters recording                                                                                                                                |
| `1`  | `uint8`  | date of parameters recording                                                                                                                                 |
| `1`  | `uint8`  | the number of digits after the decimal point for displaying energy values (`0x00` - no digits, `0x01` - `1` digit, `0x02` - `2` digits, `0x03` - `3` digits) |
| `2`  | `int16`  | numerator of the current transformation ratio                                                                                                                |
| `2`  | `int16`  | denominator of the current transformation ratio                                                                                                              |
| `2`  | `int16`  | numerator of the voltage transformation ratio                                                                                                                |
| `2`  | `int16`  | denominator of the voltage transformation ratio                                                                                                              |
| `1`  | `uint8`  | [measurement type](./GetOpParams.md#measurement-type)                                                                                                        |
| `1`  | `uint16` | minimum threshold for the `cos φ` value                                                                                                                      |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum current                                                                                                      |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum power                                                                                                        |
| `1`  | `uint8`  | timeout for relay deactivation based on `cos φ`                                                                                                              |
| `1`  | `uint8`  | `PMAX` settings, `0` - `PMAX` = `POWER_A` + `POWER_B` + `POWER_C`; `1` - `PMAX` averaged power over the integration period                                   |
| `4`  | `uint32` | [display settings 4](./GetOpParams.md#display-settings-4)                                                                                                    |

### Examples

| Field                                                                     | Value    | Hex          |
| ------------------------------------------------------------------------- | -------- | ------------ |
| command id                                                                | `31`     | `0x1f`       |
| command size                                                              | `95`     | `0x5f`       |
| maximum voltage threshold, mV                                             | `265000` | `0x00040b28` |
| minimum voltage threshold, mV                                             | `156000` | `0x00026160` |
| maximum current threshold, mA                                             | `120000` | `0x0001d4c0` |
| maximum active power threshold for tariff `T1`, Watts                     | `31800`  | `0x00007c38` |
| maximum active power threshold for tariff `T2`, Watts                     | `31800`  | `0x00007c38` |
| maximum active power threshold for tariff `T3`, Watts                     | `31800`  | `0x00007c38` |
| maximum active power threshold for tariff `T4`, Watts                     | `31800`  | `0x00007c38` |
| maximum reactive power threshold for tariff `T1`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| maximum reactive power threshold for tariff `T2`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| maximum reactive power threshold for tariff `T3`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| maximum reactive power threshold for tariff `T4`, Volt-ampere reactive    | `31800`  | `0x00007c38` |
| power averaging interval, in minutes                                      | `30`     | `0x1e`       |
| start date of the monthly billing period                                  | `1`      | `0x01`       |
| display active time                                                       | `127`    | `0x7f`       |
| display active time for each screen                                       | `7`      | `0x07`       |
| display settings 1                                                        | `?`      | `0x00001085` |
| display settings 2                                                        | `?`      | `0x00022200` |
| display settings 3                                                        | `?`      | `0x00000000` |
| relay set                                                                 | `?`      | `0x00000303` |
| serial ports set                                                          | `?`      | `0x44`       |
| integration period for energy profiles `A+`, `A-`, voltage                | `30`     | `0x1e`       |
| voltage averaging interval to detect voltage quality                      | `30`     | `0x1e`       |
| interval for tracking power off events, in minutes                        | `3`      | `0x03`       |
| reserved byte                                                             | `0`      | `0x00`       |
| timeout for relay deactivation due to poor voltage, seconds               | `5`      | `0x05`       |
| maximum threshold for the frequency of the grid voltage                   | `55`     | `0x37`       |
| minimum threshold for the frequency of the grid voltage                   | `45`     | `0x2d`       |
| year of parameters recording                                              | `0`      | `0x00`       |
| month of parameters recording                                             | `0`      | `0x00`       |
| date of parameters recording                                              | `0`      | `0x00`       |
| the number of digits after the decimal point for displaying energy values | `2`      | `0x02`       |
| numerator of the current transformation ratio                             | `1`      | `0x0001`     |
| denominator of the current transformation ratio                           | `1`      | `0x0001`     |
| numerator of the voltage transformation ratio                             | `1`      | `0x0001`     |
| denominator of the voltage transformation ratio                           | `1`      | `0x0001`     |
| measurement type                                                          | `0`      | `0x00`       |
| minimum threshold for the `cos φ` value                                   | `0`      | `0x0000`     |
| timeout for relay deactivation based on maximum current                   | `5`      | `0x05`       |
| timeout for relay deactivation based on maximum power                     | `5`      | `0x05`       |
| timeout for relay deactivation based on `cos φ`                           | `5`      | `0x05`       |
| `PMAX` settings                                                           | `5`      | `0x05`       |
| display settings 4                                                        | `?`      | `0x80060000` |

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
