# GetOperatorParameters

Request/response to get device operator parameters.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x1e` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `30`  | `0x1e` |
| command size | `0`   | `0x00` |

Command hex dump: `1e 00`


## Response

### Format

| Size | Type     | Field                                                                                                                                                          |
| ---- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x1e`                                                                                                                                            |
| `1`  | `uint8`  | command size = `74`                                                                                                                                            |
| `4`  | `uint32` | maximum voltage threshold, mV                                                                                                                                  |
| `4`  | `uint32` | minimum voltage threshold, mV                                                                                                                                  |
| `4`  | `uint32` | maximum current threshold, mA                                                                                                                                  |
| `4`  | `uint32` | maximum power threshold for tariff `T1`, Watts                                                                                                                 |
| `4`  | `uint32` | maximum power threshold for tariff `T2`, Watts                                                                                                                 |
| `4`  | `uint32` | maximum power threshold for tariff `T3`, Watts                                                                                                                 |
| `4`  | `uint32` | maximum power threshold for tariff `T4`, Watts                                                                                                                 |
| `1`  | `uint8`  | [serial ports set](#serial-ports-set) byte                                                                                                                     |
| `1`  | `uint8`  | power averaging interval, in minutes                                                                                                                           |
| `1`  | `uint8`  | start date of the monthly billing period                                                                                                                       |
| `1`  | `uint8`  | display active time                                                                                                                                            |
| `1`  | `uint8`  | display active time for each screen                                                                                                                            |
| `4`  | `uint32` | [display settings for meter readings](#display-settings-for-meter-readings)                                                                                    |
| `1`  | `uint8`  | [relay set 4](#relay-set-4)                                                                                                                                    |
| `1`  | `uint8`  | [relay set 3](#relay-set-3)                                                                                                                                    |
| `1`  | `uint8`  | [relay set 2](#relay-set-2)                                                                                                                                    |
| `1`  | `uint8`  | [relay set 1](#relay-set-1)                                                                                                                                    |
| `1`  | `uint8`  | display type on the remote display (`0` - `OBIS`, `1` - symbolic (not used))                                                                                   |
| `1`  | `uint8`  | integration period for energy profiles `A+`, `A-`, voltage VA `0`, `30` - `30`, `1`, `3` ,`5`, `10`, `15`, `60` minutes (`ten`)                                |
| `1`  | `uint8`  | voltage averaging interval `0`, `1`, `3`, `5`, `10`, `15`, `30`, `60` minutes to detect voltage quality                                                        |
| `1`  | `uint8`  | reserved byte                                                                                                                                                  |
| `1`  | `uint8`  | allowed correction interval (`15` minutes by default)                                                                                                          |
| `1`  | `uint8`  | timeout for relay shutdown upon magnetic interference, seconds                                                                                                 |
| `1`  | `uint8`  | timeout for relay activation after magnetic field removal, seconds                                                                                             |
| `1`  | `uint8`  | [define 1](#define-1)                                                                                                                                          |
| `1`  | `uint8`  | timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                                                                      |
| `1`  | `uint8`  | timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds                                         |
| `1`  | `uint8`  | timeout for relay activation upon restoration of quality voltage, seconds                                                                                      |
| `1`  | `uint8`  | timeout for relay deactivation due to poor voltage, seconds                                                                                                    |
| `1`  | `uint8`  | maximum threshold for the frequency of the grid voltage                                                                                                        |
| `1`  | `uint8`  | Minimum threshold for the frequency of the grid voltage                                                                                                        |
| `2`  | `uint16` | minimum threshold for the `cos φ` value                                                                                                                        |
| `1`  | `uint8`  | year of parameters recording                                                                                                                                   |
| `1`  | `uint8`  | month of parameters recording                                                                                                                                  |
| `1`  | `uint8`  | date of parameters recording                                                                                                                                   |
| `1`  | `uint8`  | the number of digits after the decimal point for displaying energy values (`0x00` - no digits, `0x01` - `1` digit, `0x02` - `2` digits, `0x03` - `3` digits)   |
| `1`  | `uint8`  | measurement type (`0` - active `\|A\|+`, `1` - active `A+`, `A-`)                                                                                              |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum current                                                                                                        |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum power                                                                                                          |
| `1`  | `uint8`  | timeout for relay deactivation based on `cos φ`                                                                                                                |
| `1`  | `uint8`  | `0` - `PMAX` = `POWER_A`; `1` - `PMAX` averaged power over the integration period                                                                              |
| `4`  | `uint32` | [setting for displaying meter readings on additional displays](#setting-for-displaying-meter-readings-on-additional-displays) (long press)                     |
| `1`  | `uint8`  | timeout for relay deactivation based on current inequality (`5`)                                                                                               |
| `1`  | `uint8`  | timeout for relay deactivation upon detection of power with different polarities (`5`)                                                                         |
| `1`  | `uint8`  | [relay set 5](#relay-set-5)                                                                                                                                    |
| `1`  | `uint8`  | allowed correction period, in hours (`24` hours by default). If bit `7` is `0` (default is `0`), time correction crossing the half-hour boundary is forbidden. |

### Parameters

#### display settings for meter readings

Bit mask:

| Name                           | Bit  | Description                                                             |
| ------------------------------ | ---- | ----------------------------------------------------------------------- |
| `SET_ALL_SEGMENT_DISPLAY`      | `0`  | enable display test                                                     |
| `SOFTWARE_VERSION`             | `1`  | enable software version display                                         |
| `TOTAL_ACTIVE_ENERGY`          | `2`  | enable total active energy `A+` display                                 |
| `ACTIVE_ENERGY_T1`             | `3`  | enable active energy `A+` display for tariff `T1`                       |
| `ACTIVE_ENERGY_T2`             | `4`  | enable active energy `A+` display for tariff `T2`                       |
| `ACTIVE_ENERGY_T3`             | `5`  | enable active energy `A+` display for tariff `T3`                       |
| `ACTIVE_ENERGY_T4`             | `6`  | enable active energy `A+` display for tariff `T4`                       |
| `ACTIVE_POWER_PER_PHASE`       | `7`  | enable active power consumption display in phase                        |
| `ACTIVE_POWER_IN_NEUTRAL`      | `8`  | enable active power consumption display in neutral                      |
| `CURRENT_IN_PHASE`             | `9`  | enable root mean square current display in phase                        |
| `CURRENT_IN_NEUTRAL`           | `10` | enable root mean square current display in neutral                      |
| `VOLTAGE`                      | `11` | enable root mean square voltage display                                 |
| `HOUR_MINUTE_SECOND`           | `12` | enable time display                                                     |
| `DATE_MONTH_YEAR`              | `13` | enable date display                                                     |
| `TOTAL_EXPORTED_ACTIVE_ENERGY` | `14` | enable total active energy `A-` display                                 |
| `EXPORTED_ACTIVE_ENERGY_T1`    | `15` | enable active energy `A-` display for tariff `T1`                       |
| `EXPORTED_ACTIVE_ENERGY_T2`    | `16` | enable active energy `A-` display for tariff `T2`                       |
| `EXPORTED_ACTIVE_ENERGY_T3`    | `17` | enable active energy `A-` display for tariff `T3`                       |
| `EXPORTED_ACTIVE_ENERGY_T4`    | `18` | enable active energy `A-` display for tariff `T4`                       |
| `POWER_FACTOR_PHASE_A`         | `19` | enable power factor display for phase `A` (Obis `33.7.0`)               |
| `POWER_FACTOR_PHASE_B`         | `20` | enable power factor display for phase `B` (Obis `53.7.0`)               |
| `BATTERY_VOLTAGE`              | `21` | enable battery voltage display (Obis `96.6.3`)                          |
| `POWER_THRESHOLD_T1`           | `22` | enable relay off power threshold display for tariff `T1` (Obis `5.2.1`) |
| `POWER_THRESHOLD_T2`           | `23` | enable relay off power threshold display for tariff `T2` (Obis `5.2.2`) |
| `POWER_THRESHOLD_T3`           | `24` | enable relay off power threshold display for tariff `T3` (Obis `5.2.3`) |
| `POWER_THRESHOLD_T4`           | `25` | enable relay off power threshold display for tariff `T4` (Obis `5.2.4`) |
| `CURRENT_BALANCE`              | `29` | enable current balance display                                          |
| -                              | `30` | not used                                                                |
| `AUTO_SCREEN_SCROLLING`        | `31` | enable automatic display scrolling (applies only to the main display)   |

#### relay set 4

Bit mask:

| Name                      | Bit | Description                                            |
| ------------------------- | --- | ------------------------------------------------------ |
| `RELAY_ON_TIMEOUT`        | `0` | enable after `timeoutRelayOn` timeout                  |
| `RELAY_ON_SALDO`          | `1` | enable by balance                                      |
| `RELAY_OFF_SALDO`         | `2` | disable by balance                                     |
| `RELAY_OFF_SALDO_SOFT`    | `3` | disable by balance condition                           |
| `RELAY_OFF_MAGNET`        | `4` | disable relay upon detection of magnetic field         |
| `RELAY_ON_MAGNET_TIMEOUT` | `5` | enable relay after `timeoutRelayOn` timeout (not used) |
| `RELAY_ON_MAGNET_AUTO`    | `6` | enable relay after removal of magnetic field           |

#### relay set 3

Bit mask:

| Name                     | Bit | Description                                                  |
| ------------------------ | --- | ------------------------------------------------------------ |
| `RELAY_OFF_LIM_TARIFF_1` | `1` | disable by exceeding power consumption limit for tariff `T1` |
| `RELAY_OFF_LIM_TARIFF_2` | `2` | disable by exceeding power consumption limit for tariff `T2` |
| `RELAY_OFF_LIM_TARIFF_3` | `3` | disable by exceeding power consumption limit for tariff `T3` |
| `RELAY_OFF_LIM_TARIFF_4` | `4` | disable by exceeding power consumption limit for tariff `T4` |
| `RELAY_OFF_PF_MIN`       | `5` | disable by `cos φ`                                           |

#### relay set 2

Bit mask:

| Name                 | Bit | Description                                       |
| -------------------- | --- | ------------------------------------------------- |
| `RELAY_OFF_Y`        | `0` | relay off function: `1` - enabled, `0` - disabled |
| `RELAY_OFF_CENTER`   | `1` | disable by central command                        |
| `RELAY_OFF_TARIFF_1` | `2` | disable by tariff `T1`                            |
| `RELAY_OFF_TARIFF_2` | `3` | disable by tariff `T2`                            |
| `RELAY_OFF_TARIFF_3` | `4` | disable by tariff `T3`                            |
| `RELAY_OFF_TARIFF_4` | `5` | disable by tariff `T4`                            |
| `RELAY_OFF_I_LIMIT`  | `6` | disable by exceeding load current                 |
| `RELAY_OFF_V_BAD`    | `7` | disable by poor voltage quality                   |

#### relay set 1

Bit mask:

| Name                | Bit | Description                                      |
| ------------------- | --- | ------------------------------------------------ |
| `RELAY_ON_Y`        | `0` | relay on function: `1` - enabled, `0` - disabled |
| `RELAY_ON_CENTER`   | `1` | enable by central command                        |
| `RELAY_ON_PB`       | `2` | enable by button                                 |
| `RELAY_ON_TARIFF_1` | `3` | enable by tariff `T1`                            |
| `RELAY_ON_TARIFF_2` | `4` | enable by tariff `T2`                            |
| `RELAY_ON_TARIFF_3` | `5` | enable by tariff `T3`                            |
| `RELAY_ON_TARIFF_4` | `6` | enable by tariff `T4`                            |
| `RELAY_ON_V_GOOD`   | `7` | enable by restoration of good voltage quality    |

#### define 1

Bit mask:

| Name                  | Bit | Description                                                      |
| --------------------- | --- | ---------------------------------------------------------------- |
| `BLOCK_KEY_OPTOPORT`  | `2` | `1` - optoport is unlocked by button, `0` - optoport is unlocked |
| `MAGNET_SCREEN_CONST` | `5` | `1` - constant magnetic influence screen (`104.21.017`)          |

#### setting for displaying meter readings on additional displays

Bit mask:

| Name                   | Bit      | Description                                                                                             |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------------------- |
|                        | `0`-`25` | all fields are identical to [Display settings for meter readings](#display-settings-for-meter-readings) |
| `MAGNET_INDUCTION`     | `27`     | magnet induction                                                                                        |
| `CURRENT_BALANCE`      | `29`     | enable current balance display                                                                          |
| `OPTOPORT_SPEED`       | `30`     | allows display of current optoport speed (`104.21.017`)                                                 |
| `SORT_DISPLAY_SCREENS` | `31`     | enable new display sorting                                                                              |

#### relay set 5

Bit mask:

| Name                        | Bit | Description                                                                                               |
| --------------------------- | --- | --------------------------------------------------------------------------------------------------------- |
| `RELAY_OFF_UNEQUAL_CURRENT` | `0` | relay off when unequal currents are detected                                                              |
| `RELAY_ON_UNEQUAL_CURRENT`  | `1` | relay on after being turned off due to unequal currents                                                   |
| `RELAY_OFF_BIPOLAR_POWER`   | `2` | relay off when opposite polarity powers are detected in phase and neutral (only for `G` meter)            |
| `RELAY_ON_BIPOLAR_POWER`    | `3` | relay on after being turned off due to opposite polarity powers in phase and neutral (only for `G` meter) |

#### serial ports set

Bit mask:

| Name                 | Bit    | Description                     |
| -------------------- | ------ | ------------------------------- |
| `RS485/TWI SPEED`    | `0..3` | `2` - `2400`; `0`, `4` - `9600` |
| `OPTICAL PORT SPEED` | `4..7` | `0`, `2` - `2400`; `4` - `9600` |

### Examples

| Field                                                                            | Value    | Hex          |
| -------------------------------------------------------------------------------- | -------- | ------------ |
| command id                                                                       | `30`     | `0x1e`       |
| command size                                                                     | `74`     | `0x4a`       |
| maximum voltage threshold                                                        | `265000` | `0x00040b28` |
| minimum voltage threshold                                                        | `156000` | `0x00026160` |
| maximum current threshold                                                        | `120000` | `0x0001d4c0` |
| maximum power threshold for tariff `T1`                                          | `31800`  | `0x00007c38` |
| maximum power threshold for tariff `T2`                                          | `31800`  | `0x00007c38` |
| maximum power threshold for tariff `T3`                                          | `31800`  | `0x00007c38` |
| maximum power threshold for tariff `T4`                                          | `31800`  | `0x00007c38` |
| reserved byte                                                                    | -        | `0x00`       |
| power averaging interval                                                         | `30`     | `0x1e`       |
| start date of the monthly billing period                                         | `1`      | `0x01`       |
| display active time                                                              | `127`    | `0x7f`       |
| display active time for each screen                                              | `7`      | `0x07`       |
| display settings for meter readings                                              | `?`      | `0x80003184` |
| relay set `4`                                                                    | `?`      | `0x00`       |
| relay set `3`                                                                    | `?`      | `0x00`       |
| relay set `2`                                                                    | `?`      | `0x03`       |
| relay set `1`                                                                    | `?`      | `0x03`       |
| display type on the remote display                                               | `0`      | `0x00`       |
| integration period for energy profiles (`ten`)                                   | `0`      | `0x00`       |
| timeout refresh                                                                  | `240`    | `0x00f0`     |
| allowed correction interval                                                      | `15`     | `0x0f`       |
| timeout for relay shutdown upon magnetic interference                            | `5`      | `0x05`       |
| timeout for relay activation after magnetic field removal                        | `5`      | `0x05`       |
| define `1`                                                                       | `?`      | `0x00`       |
| timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI` | `1`      | `0x01`       |
| timeout for relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`           | `0`      | `0x00`       |
| timeout for relay activation upon restoration of quality voltage                 | `5`      | `0x05`       |
| timeout for relay deactivation due to poor voltage                               | `5`      | `0x05`       |
| maximum threshold for the frequency of the grid voltage                          | `55`     | `0x37`       |
| minimum threshold for the frequency of the grid voltage                          | `45`     | `0x2d`       |
| minimum threshold for the `cos φ` value                                          | `0`      | `0x00`       |
| year of parameters recording                                                     | `0`      | `0x00`       |
| month of parameters recording                                                    | `0`      | `0x00`       |
| date of parameters recording                                                     | `0`      | `0x00`       |
| the number of digits after the decimal point for displaying energy values        | `2`      | `0x02`       |
| measurement type                                                                 | `0`      | `0x00`       |
| timeout for relay deactivation based on maximum current                          | `5`      | `0x05`       |
| timeout for relay deactivation based on maximum power                            | `5`      | `0x05`       |
| timeout for relay deactivation based on `cos φ`                                  | `5`      | `0x05`       |
| averaged power over the integration period                                       | `1`      | `0x01`       |
| setting for displaying meter readings on additional displays                     | `?`      | `0x08383fff` |
| timeout for relay deactivation based on current inequality                       | `5`      | `0x05`       |
| timeout for relay deactivation upon detection of power with different polarities | `5`      | `0x05`       |
| relay set `5`                                                                    | `?`      | `0x00`       |
| allowed correction period                                                        | `24`     | `0x18`       |

Command hex dump: `1e 4a 00040b28 00026160 0001d4c0 00007c38 00007c38 00007c38 00007c38 00 1e 01 7f 07 80003184 00 00 03 03 00 00 00f0 0f 05 05 00 01 00 05 05 37 2d 00  00 00 00 00 02 00 05 05 05  01 08383fff 05 05 00 18`


## See also

* [Access level](../basics.md#command-access-level)
