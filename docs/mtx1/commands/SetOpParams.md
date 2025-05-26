# SetOpParams

Request/response to set device operator parameters.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                                                                                                          |
| ---- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x1f`                                                                                                                                            |
| `1`  | `uint8`  | command size = `74`                                                                                                                                            |
| `1`  | `uint32` | Maximum voltage threshold, mV                                                                                                                                  |
| `1`  | `uint32` | Minimum voltage threshold, mV                                                                                                                                  |
| `1`  | `uint32` | Maximum current threshold, mA                                                                                                                                  |
| `1`  | `uint32` | Maximum power threshold for tariff `T1`, Watts                                                                                                                 |
| `1`  | `uint32` | Maximum power threshold for tariff `T2`, Watts                                                                                                                 |
| `1`  | `uint32` | Maximum power threshold for tariff `T3`, Watts                                                                                                                 |
| `1`  | `uint32` | Maximum power threshold for tariff `T4`, Watts                                                                                                                 |
| `1`  | `uint8`  | Reserved byte                                                                                                                                                  |
| `1`  | `uint8`  | Power averaging interval, in minutes                                                                                                                           |
| `1`  | `uint8`  | Start date of the monthly billing period                                                                                                                       |
| `1`  | `uint8`  | Display active time                                                                                                                                            |
| `1`  | `uint8`  | Display active time for each screen                                                                                                                            |
| `1`  | `uint32` | [Display settings for meter readings](#display-settings-for-meter-readings)                                                                                    |
| `1`  | `uint8`  | [Relay set 4](#relay-set-4)                                                                                                                                    |
| `1`  | `uint8`  | [Relay set 3](#relay-set-3)                                                                                                                                    |
| `1`  | `uint8`  | [Relay set 2](#relay-set-2)                                                                                                                                    |
| `1`  | `uint8`  | [Relay set 1](#relay-set-1)                                                                                                                                    |
| `1`  | `uint8`  | Display type on the remote display (`0` - `OBIS`, `1` - symbolic (not used))                                                                                   |
| `1`  | `uint8`  | Integration period for energy profiles `A+`, `A-`, voltage VA `0`, `30` - `30`, `1`, `3` ,`5`, `10`, `15`, `60` minutes (`ten`)                                |
| `1`  | `uint8`  | Voltage averaging interval `0`, `1`, `3`, `5`, `10`, `15`, `30`, `60` minutes to detect voltage quality                                                        |
| `1`  | `uint8`  | Reserved byte                                                                                                                                                  |
| `1`  | `uint8`  | Allowed correction interval (`15` minutes by default)                                                                                                          |
| `1`  | `uint8`  | Timeout for relay shutdown upon magnetic interference, seconds                                                                                                 |
| `1`  | `uint8`  | Timeout for relay activation after magnetic field removal, seconds                                                                                             |
| `1`  | `uint8`  | [Define 1](#define-1)                                                                                                                                          |
| `1`  | `uint8`  | Timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                                                                      |
| `1`  | `uint8`  | Timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds                                         |
| `1`  | `uint8`  | Timeout for relay activation upon restoration of quality voltage, seconds                                                                                      |
| `1`  | `uint8`  | Timeout for relay deactivation due to poor voltage, seconds                                                                                                    |
| `1`  | `uint8`  | Maximum threshold for the frequency of the grid voltage                                                                                                        |
| `1`  | `uint8`  | Minimum threshold for the frequency of the grid voltage                                                                                                        |
| `1`  | `uint16` | Minimum threshold for the `cos φ` value                                                                                                                        |
| `1`  | `uint8`  | Year of parameters recording                                                                                                                                   |
| `1`  | `uint8`  | Month of parameters recording                                                                                                                                  |
| `1`  | `uint8`  | Date of parameters recording                                                                                                                                   |
| `1`  | `uint8`  | The number of digits after the decimal point for displaying energy values (`0x00` - no digits, `0x01` - `1` digit, `0x02` - `2` digits, `0x03` - `3` digits)   |
| `1`  | `uint8`  | Measurement type (`0` - active `\|A\|+`, `1` - active `A+`, `A-`)                                                                                              |
| `1`  | `uint8`  | Timeout for relay deactivation based on maximum current                                                                                                        |
| `1`  | `uint8`  | Timeout for relay deactivation based on maximum power                                                                                                          |
| `1`  | `uint8`  | Timeout for relay deactivation based on `cos φ`                                                                                                                |
| `1`  | `uint8`  | `0` - `PMAX` = `POWER_A`; `1` - `PMAX` averaged power over the integration period                                                                              |
| `1`  | `uint32` | [Setting for displaying meter readings on additional displays](#setting-for-displaying-meter-readings-on-additional-displays) (long press)                     |
| `1`  | `uint8`  | Timeout for relay deactivation based on current inequality (`5`)                                                                                               |
| `1`  | `uint8`  | Timeout for relay deactivation upon detection of power with different polarities (`5`)                                                                         |
| `1`  | `uint8`  | [Relay set 5](#relay-set-5)                                                                                                                                    |
| `1`  | `uint8`  | Allowed correction period, in hours (`24` hours by default). If bit `7` is `0` (default is `0`), time correction crossing the half-hour boundary is forbidden. |

### Parameters

#### Display settings for meter readings

Bit mask:

| Name                           | Bit  | Description                                                             |
| ------------------------------ | ---- | ----------------------------------------------------------------------- |
| `SET_ALL_SEGMENT_DISPLAY`      | `0`  | Enable display test                                                     |
| `SOFTWARE_VERSION`             | `1`  | Enable software version display                                         |
| `TOTAL_ACTIVE_ENERGY`          | `2`  | Enable total active energy `A+` display                                 |
| `ACTIVE_ENERGY_T1`             | `3`  | Enable active energy `A+` display for tariff `T1`                       |
| `ACTIVE_ENERGY_T2`             | `4`  | Enable active energy `A+` display for tariff `T2`                       |
| `ACTIVE_ENERGY_T3`             | `5`  | Enable active energy `A+` display for tariff `T3`                       |
| `ACTIVE_ENERGY_T4`             | `6`  | Enable active energy `A+` display for tariff `T4`                       |
| `ACTIVE_POWER_PER_PHASE`       | `7`  | Enable active power consumption display in phase                        |
| `ACTIVE_POWER_IN_NEUTRAL`      | `8`  | Enable active power consumption display in neutral                      |
| `CURRENT_IN_PHASE`             | `9`  | Enable root mean square current display in phase                        |
| `CURRENT_IN_NEUTRAL`           | `10` | Enable root mean square current display in neutral                      |
| `VOLTAGE`                      | `11` | Enable root mean square voltage display                                 |
| `HOUR_MINUTE_SECOND`           | `12` | Enable time display                                                     |
| `DATE_MONTH_YEAR`              | `13` | Enable date display                                                     |
| `TOTAL_EXPORTED_ACTIVE_ENERGY` | `14` | Enable total active energy `A-` display                                 |
| `EXPORTED_ACTIVE_ENERGY_T1`    | `15` | Enable active energy `A-` display for tariff `T1`                       |
| `EXPORTED_ACTIVE_ENERGY_T2`    | `16` | Enable active energy `A-` display for tariff `T2`                       |
| `EXPORTED_ACTIVE_ENERGY_T3`    | `17` | Enable active energy `A-` display for tariff `T3`                       |
| `EXPORTED_ACTIVE_ENERGY_T4`    | `18` | Enable active energy `A-` display for tariff `T4`                       |
| `POWER_COEFFICIENT_PHASE_A`    | `19` | Enable power factor display on channel `A` (Obis `33.7.0`)              |
| `POWER_COEFFICIENT_PHASE_B`    | `20` | Enable power factor display on channel `B` (Obis `53.7.0`)              |
| `BATTERY_VOLTAGE`              | `21` | Enable battery voltage display (Obis `96.6.3`)                          |
| `POWER_THRESHOLD_T1`           | `22` | Enable relay off power threshold display for tariff `T1` (Obis `5.2.1`) |
| `POWER_THRESHOLD_T2`           | `23` | Enable relay off power threshold display for tariff `T2` (Obis `5.2.2`) |
| `POWER_THRESHOLD_T3`           | `24` | Enable relay off power threshold display for tariff `T3` (Obis `5.2.3`) |
| `POWER_THRESHOLD_T4`           | `25` | Enable relay off power threshold display for tariff `T4` (Obis `5.2.4`) |
| `CURRENT_BALANCE`              | `29` | Enable current balance display                                          |
| -                              | `30` | Not used                                                                |
| `AUTO_SCREEN_SCROLLING`        | `31` | Enable automatic display scrolling (applies only to the main display)   |

#### Relay set 4

Bit mask:

| Name                      | Bit | Description                                            |
| ------------------------- | --- | ------------------------------------------------------ |
| `RELAY_ON_TIMEOUT`        | `0` | Enable after `timeoutRelayOn` timeout                  |
| `RELAY_ON_SALDO`          | `1` | Enable by balance                                      |
| `RELAY_OFF_SALDO`         | `2` | Disable by balance                                     |
| `RELAY_OFF_SALDO_SOFT`    | `3` | Disable by balance condition                           |
| `RELAY_OFF_MAGNET`        | `4` | Disable relay upon detection of magnetic field         |
| `RELAY_ON_MAGNET_TIMEOUT` | `5` | Enable relay after `timeoutRelayOn` timeout (not used) |
| `RELAY_ON_MAGNET_AUTO`    | `6` | Enable relay after removal of magnetic field           |

#### Relay set 3

Bit mask:

| Name                     | Bit | Description                                                  |
| ------------------------ | --- | ------------------------------------------------------------ |
| -                        | `0` | Reserved bit                                                 |
| `RELAY_OFF_LIM_TARIFF_1` | `1` | Disable by exceeding power consumption limit for tariff `T1` |
| `RELAY_OFF_LIM_TARIFF_2` | `2` | Disable by exceeding power consumption limit for tariff `T2` |
| `RELAY_OFF_LIM_TARIFF_3` | `3` | Disable by exceeding power consumption limit for tariff `T3` |
| `RELAY_OFF_LIM_TARIFF_4` | `4` | Disable by exceeding power consumption limit for tariff `T4` |
| `RELAY_OFF_PF_MIN`       | `5` | Disable by `cos φ`                                           |

#### Relay set 2

Bit mask:

| Name                 | Bit | Description                                       |
| -------------------- | --- | ------------------------------------------------- |
| `RELAY_OFF_Y`        | `0` | Relay off function: `1` - enabled, `0` - disabled |
| `RELAY_OFF_CENTER`   | `1` | Disable by central command                        |
| `RELAY_OFF_TARIFF_1` | `2` | Disable by tariff `T1`                            |
| `RELAY_OFF_TARIFF_2` | `3` | Disable by tariff `T2`                            |
| `RELAY_OFF_TARIFF_3` | `4` | Disable by tariff `T3`                            |
| `RELAY_OFF_TARIFF_4` | `5` | Disable by tariff `T4`                            |
| `RELAY_OFF_I_LIMIT`  | `6` | Disable by exceeding load current                 |
| `RELAY_OFF_V_BAD`    | `7` | Disable by poor voltage quality                   |

#### Relay set 1

Bit mask:

| Name                | Bit | Description                                      |
| ------------------- | --- | ------------------------------------------------ |
| `RELAY_ON_Y`        | `0` | Relay on function: `1` - enabled, `0` - disabled |
| `RELAY_ON_CENTER`   | `1` | Enable by central command                        |
| `RELAY_ON_PB`       | `2` | Enable by button                                 |
| `RELAY_ON_TARIFF_1` | `3` | Enable by tariff `T1`                            |
| `RELAY_ON_TARIFF_2` | `4` | Enable by tariff `T2`                            |
| `RELAY_ON_TARIFF_3` | `5` | Enable by tariff `T3`                            |
| `RELAY_ON_TARIFF_4` | `6` | Enable by tariff `T4`                            |
| `RELAY_ON_V_GOOD`   | `7` | Enable by restoration of good voltage quality    |

#### Define 1

Bit mask:

| Name                  | Bit | Description                                                            |
| --------------------- | --- | ---------------------------------------------------------------------- |
| `BLOCK_KEY_OPTOPORT`  | `2` | `1` - optoport is unlocked by button, `0` - optoport is unlocked (`0`) |
| `MAGNET_SCREEN_CONST` | `5` | `1` – constant magnetic influence screen (`104.21.017`)                |

#### Setting for displaying meter readings on additional displays

Bit mask:

| Name                   | Bit      | Description                                                                                             |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------------------- |
|                        | `0`-`25` | All fields are identical to [Display settings for meter readings](#display-settings-for-meter-readings) |
| `MAGNET_INDUCTION`     | `27`     | Magnet induction                                                                                        |
| `CURRENT_BALANCE`      | `29`     | Enable current balance display                                                                          |
| `OPTOPORT_SPEED`       | `30`     | Allows display of current optoport speed (`104.21.017`)                                                 |
| `SORT_DISPLAY_SCREENS` | `31`     | Enable new display sorting                                                                              |

#### Relay set 5

Bit mask:

| Name                        | Bit | Description                                                                                               |
| --------------------------- | --- | --------------------------------------------------------------------------------------------------------- |
| `RELAY_OFF_UNEQUAL_CURRENT` | `0` | Relay off when unequal currents are detected                                                              |
| `RELAY_ON_UNEQUAL_CURRENT`  | `1` | Relay on after being turned off due to unequal currents                                                   |
| `RELAY_OFF_BIPOLAR_POWER`   | `2` | Relay off when opposite polarity powers are detected in phase and neutral (only for `G` meter)            |
| `RELAY_ON_BIPOLAR_POWER`    | `3` | Relay on after being turned off due to opposite polarity powers in phase and neutral (only for `G` meter) |

### Examples

| Field                                                                            | Value    | Hex          |
| -------------------------------------------------------------------------------- | -------- | ------------ |
| command id                                                                       | `31`     | `0x1f`       |
| command size                                                                     | `74`     | `0x4a`       |
| Maximum voltage threshold                                                        | `265000` | `0x00040b28` |
| Minimum voltage threshold                                                        | `156000` | `0x00026160` |
| Maximum current threshold                                                        | `120000` | `0x0001d4c0` |
| Maximum power threshold for tariff `T1`                                          | `31800`  | `0x00007c38` |
| Maximum power threshold for tariff `T2`                                          | `31800`  | `0x00007c38` |
| Maximum power threshold for tariff `T3`                                          | `31800`  | `0x00007c38` |
| Maximum power threshold for tariff `T4`                                          | `31800`  | `0x00007c38` |
| Reserved byte                                                                    | -        | `0x00`       |
| Power averaging interval                                                         | `30`     | `0x1e`       |
| Start date of the monthly billing period                                         | `1`      | `0x01`       |
| Display active time                                                              | `127`    | `0x7f`       |
| Display active time for each screen                                              | `7`      | `0x07`       |
| Display settings for meter readings                                              | `?`      | `0x80003184` |
| Relay set 4                                                                      | `?`      | `0x00`       |
| Relay set 3                                                                      | `?`      | `0x00`       |
| Relay set 2                                                                      | `?`      | `0x03`       |
| Relay set 1                                                                      | `?`      | `0x03`       |
| Display type on the remote display                                               | `0`      | `0x00`       |
| Integration period for energy profiles (`ten`)                                   | `0`      | `0x00`       |
| Timeout refresh                                                                  | `240`    | `0x00f0`     |
| Allowed correction interval                                                      | `15`     | `0x0f`       |
| Timeout for relay shutdown upon magnetic interference                            | `5`      | `0x05`       |
| Timeout for relay activation after magnetic field removal                        | `5`      | `0x05`       |
| Define 1                                                                         | `?`      | `0x00`       |
| Timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI` | `1`      | `0x01`       |
| Timeout for relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`           | `0`      | `0x00`       |
| Timeout for relay activation upon restoration of quality voltage                 | `5`      | `0x05`       |
| Timeout for relay deactivation due to poor voltage                               | `5`      | `0x05`       |
| Maximum threshold for the frequency of the grid voltage                          | `55`     | `0x37`       |
| Minimum threshold for the frequency of the grid voltage                          | `45`     | `0x2d`       |
| Minimum threshold for the `cos φ` value                                          | `0`      | `0x00`       |
| Year of parameters recording                                                     | `0`      | `0x00`       |
| Month of parameters recording                                                    | `0`      | `0x00`       |
| Date of parameters recording                                                     | `0`      | `0x00`       |
| The number of digits after the decimal point for displaying energy values        | `2`      | `0x02`       |
| Measurement type                                                                 | `0`      | `0x00`       |
| Timeout for relay deactivation based on maximum current                          | `5`      | `0x05`       |
| Timeout for relay deactivation based on maximum power                            | `5`      | `0x05`       |
| Timeout for relay deactivation based on `cos φ`                                  | `5`      | `0x05`       |
| Averaged power over the integration period                                       | `1`      | `0x01`       |
| Setting for displaying meter readings on additional displays                     | `?`      | `0x08383fff` |
| Timeout for relay deactivation based on current inequality                       | `5`      | `0x05`       |
| Timeout for relay deactivation upon detection of power with different polarities | `5`      | `0x05`       |
| Relay set 5                                                                      | `?`      | `0x00`       |
| Allowed correction period                                                        | `24`     | `0x18`       |

Command hex dump: `1f 4a 00040b28 00026160 0001d4c0 00007c38 00007c38 00007c38 00007c38 00 1e 01 7f 07 80003184 00 00 03 03 00 00 00f0 0f 05 05 00 01 00 05 05 37 2d 00  00 00 00 00 02 00 05 05 05  01 08383fff 05 05 00 18`


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
