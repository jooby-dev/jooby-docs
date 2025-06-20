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

Message hex dump: `1e 00`


## Response

### Format

| Size | Type     | Field                                                                                                                                                               |
| ---- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x1e`                                                                                                                                                 |
| `1`  | `uint8`  | command size = `95`                                                                                                                                                 |
| `4`  | `uint32` | maximum voltage threshold, mV                                                                                                                                       |
| `4`  | `uint32` | minimum voltage threshold, mV                                                                                                                                       |
| `4`  | `uint32` | maximum current threshold, mA                                                                                                                                       |
| `4`  | `uint32` | maximum active power threshold for tariff `T1`, Watts                                                                                                               |
| `4`  | `uint32` | maximum active power threshold for tariff `T2`, Watts                                                                                                               |
| `4`  | `uint32` | maximum active power threshold for tariff `T3`, Watts                                                                                                               |
| `4`  | `uint32` | maximum active power threshold for tariff `T4`, Watts                                                                                                               |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T1`, volt-ampere reactive                                                                                              |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T2`, volt-ampere reactive                                                                                              |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T3`, volt-ampere reactive                                                                                              |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T4`, volt-ampere reactive                                                                                              |
| `1`  | `uint8`  | power averaging interval, in minutes                                                                                                                                |
| `1`  | `uint8`  | start date of the monthly billing period                                                                                                                            |
| `1`  | `uint8`  | display active time                                                                                                                                                 |
| `1`  | `uint8`  | display active time for each screen                                                                                                                                 |
| `4`  | `uint32` | [display settings 1](#display-settings-1)                                                                                                                           |
| `4`  | `uint32` | [display settings 2](#display-settings-2)                                                                                                                           |
| `4`  | `uint32` | [display settings 3](#display-settings-3)                                                                                                                           |
| `4`  | `uint32` | [relay set](#relay-set)                                                                                                                                             |
| `1`  | `uint8`  | [serial ports set](#serial-ports-set)                                                                                                                               |
| `1`  | `uint8`  | integration period for energy profiles `A+`, `A-`, voltage VA , `0`, `30` - `30`, `1`, `3`, `5`, `10`, `15`, `60` minutes (`ten`)                                   |
| `1`  | `uint8`  | voltage averaging interval `0`, `1`, `3`, `5`, `10`, `15`, `30`, `60` minutes to detect voltage quality                                                             |
| `1`  | `uint8`  | reserved byte                                                                                                                                                       |
| `1`  | `uint8`  | interval for tracking power off events, in minutes                                                                                                                  |
| `1`  | `uint8`  | reserved byte                                                                                                                                                       |
| `1`  | `uint8`  | timeout for relay deactivation due to poor voltage, seconds                                                                                                         |
| `1`  | `unt8`   | maximum threshold for the frequency of the grid voltage                                                                                                             |
| `1`  | `unt8`   | minimum threshold for the frequency of the grid voltage                                                                                                             |
| `1`  | `uint8`  | year of parameters recording                                                                                                                                        |
| `1`  | `uint8`  | month of parameters recording                                                                                                                                       |
| `1`  | `uint8`  | date of parameters recording                                                                                                                                        |
| `1`  | `uint8`  | the number of digits after the decimal point for displaying energy values<br>`0x00` - no digits<br>`0x01` - `1` digit<br>`0x02` - `2` digits<br>`0x03` - `3` digits |
| `2`  | `int16`  | numerator of the current transformation ratio                                                                                                                       |
| `2`  | `int16`  | denominator of the current transformation ratio                                                                                                                     |
| `2`  | `int16`  | numerator of the voltage transformation ratio                                                                                                                       |
| `2`  | `int16`  | denominator of the voltage transformation ratio                                                                                                                     |
| `1`  | `uint8`  | [measurement type](#measurement-type)                                                                                                                               |
| `2`  | `uint16` | minimum threshold for the `cos φ` value                                                                                                                             |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum current                                                                                                             |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum power                                                                                                               |
| `1`  | `uint8`  | timeout for relay deactivation based on `cos φ`                                                                                                                     |
| `1`  | `uint8`  | `PMAX` settings<br>`0` - `PMAX` = `POWER_A` + `POWER_B` + `POWER_C`<br>`1` - `PMAX` averaged power over the integration period                                      |
| `4`  | `uint32` | [display settings 4](#display-settings-4)                                                                                                                           |

### Parameters

#### display settings 1

Bit mask:

| Name                                      | Bit  | Description                                                                                                                                                |
| ----------------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `SET_ALL_SEGMENT_DISPLAY`                 | `0`  | enable display test                                                                                                                                        |
| `SOFTWARE_VERSION`                        | `1`  | enable software version display                                                                                                                            |
| `TOTAL_ACTIVE_ENERGY`                     | `2`  | enable display of total active energy `A+` across all tariffs, OBIS: `1.8.0`                                                                               |
| `ACTIVE_ENERGY_T1`                        | `3`  | enable display of active energy `A+` for tariff `T1`, OBIS: `1.8.1`                                                                                        |
| `ACTIVE_ENERGY_T2`                        | `4`  | enable display of active energy `A+` for tariff `T2`. OBIS: `1.8.2`                                                                                        |
| `ACTIVE_ENERGY_T3`                        | `5`  | enable display of active energy `A+` for tariff `T3`. OBIS: `1.8.3`                                                                                        |
| `ACTIVE_ENERGY_T4`                        | `6`  | enable display of active energy `A+` for tariff `T4`. OBIS: `1.8.4`                                                                                        |
| `TOTAL_REACTIVE_ENERGY`                   | `7`  | enable display of inductive reactive energy `R+` total across all tariffs, OBIS: `3.8.0` (for meter type `R`); `A+R+`, OBIS: `5.8.0` (for meter type `G`)  |
| `REACTIVE_ENERGY_T1`                      | `8`  | enable display of inductive reactive energy `R+` for tariff `T1`, OBIS: `3.8.1` (for meter type `R`); `A+R+`, OBIS: `5.8.1` (for meter type `G`)           |
| `REACTIVE_ENERGY_T2`                      | `9`  | enable display inductive reactive energy `R+` for tariff `T2`, OBIS: `3.8.2` (for meter type `R`); `A+R+`, OBIS: `5.8.2` (for meter type `G`)              |
| `REACTIVE_ENERGY_T3`                      | `10` | enable display inductive reactive energy `R+` for tariff `T3`, OBIS: `3.8.3` (for meter type `R`); `A+R+`, OBIS: `5.8.3` (for meter type `G`)              |
| `REACTIVE_ENERGY_T4`                      | `11` | enable display inductive reactive energy `R+` for tariff `T4`, OBIS: `3.8.4` (for meter type `R`); `A+R+`, OBIS: `5.8.4` (for meter type `G`)              |
| `TOTAL_NEGATIVE_REACTIVE_ENERGY`          | `12` | enable display of capacitive reactive energy `R−` total across all tariffs, OBIS: `4.8.0` (for meter type `R`), `A+R−`, OBIS: `8.8.0` (for meter type `G`) |
| `NEGATIVE_REACTIVE_ENERGY_T1`             | `13` | enable display of capacitive reactive energy `R−` for tariff `T1`, OBIS: `4.8.1` (for meter type `R`), `A+R−`, OBIS: `8.8.1` (for meter type `G`)          |
| `NEGATIVE_REACTIVE_ENERGY_T2`             | `14` | enable display of capacitive reactive energy `R−` for tariff `T2`, OBIS: `4.8.2` (for meter type `R`), `A+R−`, OBIS: `8.8.2` (for meter type `G`)          |
| `NEGATIVE_REACTIVE_ENERGY_T3`             | `15` | enable display of capacitive reactive energy `R−` for tariff `T3`, OBIS: `4.8.3` (for meter type `R`), `A+R−`, OBIS: `8.8.3` (for meter type `G`)          |
| `NEGATIVE_REACTIVE_ENERGY_T4`             | `16` | enable display of capacitive reactive energy `R−` for tariff `T4`, OBIS: `4.8.4` (for meter type `R`), `A+R−`, OBIS: `8.8.4` (for meter type `G`)          |
| `TOTAL_EXPORTED_ACTIVE_ENERGY`            | `17` | enable display of total active energy `A-`, OBIS: `2.8.0`                                                                                                  |
| `EXPORTED_ACTIVE_ENERGY_T1`               | `18` | enable display of active energy `A-` for tariff `T1`, OBIS: `2.8.1`                                                                                        |
| `EXPORTED_ACTIVE_ENERGY_T2`               | `19` | enable display of active energy `A-` for tariff `T2`. OBIS: `2.8.2`                                                                                        |
| `EXPORTED_ACTIVE_ENERGY_T3`               | `20` | enable display of active energy `A-` for tariff `T3`. OBIS: `2.8.3`                                                                                        |
| `EXPORTED_ACTIVE_ENERGY_T4`               | `21` | enable display of active energy `A-` for tariff `T4`. OBIS: `2.8.4`                                                                                        |
| `TOTAL_EXPORTED_REACTIVE_ENERGY`          | `22` | enable display of combined exported active and imported reactive energy `A-R+` across all tariffs, OBIS: `6.8.0` (for meter type `G` only)                 |
| `EXPORTED_REACTIVE_ENERGY_T1`             | `23` | enable display of combined exported active and imported reactive energy `A-R+` for tariff `T1`, OBIS: `6.8.1` (for meter type `G` only)                    |
| `EXPORTED_REACTIVE_ENERGY_T2`             | `24` | enable display of combined exported active and imported reactive energy `A-R+` for tariff `T2`, OBIS: `6.8.2` (for meter type `G` only)                    |
| `EXPORTED_REACTIVE_ENERGY_T3`             | `25` | enable display of combined exported active and imported reactive energy `A-R+` for tariff `T3`, OBIS: `6.8.4` (for meter type `G` only)                    |
| `EXPORTED_REACTIVE_ENERGY_T4`             | `26` | enable display of combined exported active and imported reactive energy `A-R+` for tariff `T4`, OBIS: `6.8.4` (for meter type `G` only)                    |
| `TOTAL_EXPORTED_NEGATIVE_REACTIVE_ENERGY` | `27` | enable display of combined exported active and exported reactive energy `A-R-` across all tariffs, OBIS: `7.8.0` (for meter type `G` only)                 |
| `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T1`    | `28` | enable display of combined exported active and exported reactive energy `A-R-` for tariff `T1`, OBIS: `7.8.1` (for meter type `G` only)                    |
| `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T2`    | `29` | enable display of combined exported active and exported reactive energy `A-R-` for tariff `T2`, OBIS: `7.8.2` (for meter type `G` only)                    |
| `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T3`    | `30` | enable display of combined exported active and exported reactive energy `A-R-` for tariff `T3`, OBIS: `7.8.3` (for meter type `G` only)                    |
| `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T4`    | `31` | enable display of combined exported active and exported reactive energy `A-R-`for tariff `T4`, OBIS: `7.8.4` (for meter type `G` only)                     |

#### display settings 2

Bit mask:

| Name                            | Bit  | Description                                                                                                                                 |
| ------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `CURRENT_IN_PHASE_A`            | `0`  | enable display of phase `A` current. OBIS: `31.7.0`                                                                                         |
| `CURRENT_IN_PHASE_B`            | `1`  | enable display of phase `B` current. OBIS: `51.7.0`                                                                                         |
| `CURRENT_IN_PHASE_C`            | `2`  | enable display of phase `C` current. OBIS: `71.7.0`                                                                                         |
| `CURRENT_IN_NEUTRAL`            | `3`  | enable display of neutral current. OBIS: `91.7.0`                                                                                           |
| `VOLTAGE_IN_PHASE_A`            | `4`  | enable display of phase `A` voltage. OBIS: `32.7.0`                                                                                         |
| `VOLTAGE_IN_PHASE_B`            | `5`  | enable display of phase `B` voltage. OBIS: `52.7.0`                                                                                         |
| `VOLTAGE_IN_PHASE_C`            | `6`  | enable display of phase `C` voltage. OBIS: `72.7.0`                                                                                         |
| `BATTERY_VOLTAGE`               | `7`  | enable display of battery voltage                                                                                                           |
| `SUPPLY_FREQUENCY`              | `8`  | enable display of supply frequency. OBIS: `14.7.0`                                                                                          |
| `TOTAL_ACTIVE_POWER`            | `9`  | enable display of total active power across all phases - `P`, OBIS: `1.7.0` (for meter type `R`), `P±`, OBIS: `16.7.0` (for meter type `G`) |
| `ACTIVE_POWER_PHASE_A`          | `10` | enable display of active power for phase `A` - `P`, OBIS: `21.7.0` (for meter type `R`), `P±`, OBIS: `36.7.0` (for meter type `G`)          |
| `ACTIVE_POWER_PHASE_B`          | `11` | enable display of active power for phase `B` - `P`, OBIS: `41.7.0` (for meter type `R`), `P±`, OBIS: `56.7.0` (for meter type `G`)          |
| `ACTIVE_POWER_PHASE_C`          | `12` | enable display of active power for phase `C` - `P`, OBIS: `61.7.0` (for meter type `R`), `P±`, OBIS: `76.7.0` (for meter type `G`)          |
| `TOTAL_REACTIVE_POWER_QPLUS`    | `13` | enable display of total inductive reactive power across all phases `QI+QII`, OBIS: `3.7.0`                                                  |
| `REACTIVE_POWER_QPLUS_PHASE_A`  | `14` | enable display of total inductive reactive power for phase `A` `QI+QII`, OBIS: `23.7.0`                                                     |
| `REACTIVE_POWER_QPLUS_PHASE_B`  | `15` | enable display of total inductive reactive power for phase `B` `QI+QII`, OBIS: `43.7.0`                                                     |
| `REACTIVE_POWER_QPLUS_PHASE_C`  | `16` | enable display of total inductive reactive power for phase `C` `QI+QII`, OBIS: `63.7.0`                                                     |
| `TOTAL_REACTIVE_POWER_QMINUS`   | `17` | enable display of total capacitive reactive power across all phases `QIII+QIV`, OBIS: `4.7.0`                                               |
| `REACTIVE_POWER_QMINUS_PHASE_A` | `18` | enable display of total capacitive reactive power for phase `A` `QIII+QIV`, OBIS: `24.7.0`                                                  |
| `REACTIVE_POWER_QMINUS_PHASE_B` | `19` | enable display of total capacitive reactive power for phase `B` `QIII+QIV`, OBIS: `44.7.0`                                                  |
| `REACTIVE_POWER_QMINUS_PHASE_C` | `20` | enable display of total capacitive reactive power for phase `C` `QIII+QIV`, OBIS: `64.7.0`                                                  |
| `TOTAL_POWER_FACTOR`            | `21` | enable display of total power factor (`cos φ`) for all phases, OBIS: `13.7.0`                                                               |
| `POWER_FACTOR_PHASE_A`          | `22` | enable display of power factor (`cos φ`) for phase `A`. OBIS: `33.7.0`                                                                      |
| `POWER_FACTOR_PHASE_B`          | `23` | enable display of power factor (`cos φ`) for phase `A`. OBIS: `53.7.0`                                                                      |
| `POWER_FACTOR_PHASE_C`          | `24` | enable display of power factor (`cos φ`) for phase `C`. OBIS: `73.7.0`                                                                      |
| `TOTAL_APPARENT_QPLUS_POWER`    | `25` | enable display of total positive apparent power across all phases, `QI+QIV`, OBIS: `9.7.0`                                                  |
| `APPARENT_POWER_QPLUS_PHASE_A`  | `26` | enable display of positive apparent power for phase `A`, `QI+QIV`, OBIS: `29.7.0`                                                           |
| `APPARENT_POWER_QPLUS_PHASE_B`  | `27` | enable display of positive apparent power for phase `B`, `QI+QIV`, OBIS: `49.7.0`                                                           |
| `APPARENT_POWER_QPLUS_PHASE_C`  | `28` | enable display of positive apparent power for phase `C`, `QI+QIV`, OBIS: `69.7.0`                                                           |
| `TOTAL_APPARENT_POWER_QMINUS`   | `29` | enable display of total negative apparent power across all phases, `QII+QIII`, OBIS: `10.7.0`                                               |
| `APPARENT_POWER_QMINUS_PHASE_A` | `30` | enable display of negative apparent power for phase `A`, `QII+QIII`, OBIS: `30.7.0`                                                         |
| `APPARENT_POWER_QMINUS_PHASE_B` | `31` | enable display of negative apparent power for phase `B`, `QII+QIII`, OBIS: `50.7.0`                                                         |

#### display settings 3

Bit mask:

| Name                                    | Bit  | Description                                                                                                                                               |
| --------------------------------------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `APPARENT_POWER_QMINUS_PHASE_C`         | `0`  | enable display of negative apparent power for phase `C`, `QII+QIII`, OBIS: `70.7.0`                                                                       |
| `MAX_ACTIVE_POWER_DAY_T1`               | `1`  | enable display of maximum daily active power for tariff `T1` - `\|P\|`, OBIS: `15.26.1` (for meter type `R`); `P+`, OBIS: `1.26.1` (for meter type G`)    |
| `MAX_ACTIVE_POWER_DAY_T2`               | `2`  | enable display of maximum daily active power for tariff `T2` - `\|P\|`, OBIS: `15.26.2` (for meter type `R`); `P+`, OBIS: `1.26.2` (for meter type G`)    |
| `MAX_ACTIVE_POWER_DAY_T3`               | `3`  | enable display of maximum daily active power for tariff `T3` - `\|P\|`, OBIS: `15.26.3` (for meter type `R`); `P+`, OBIS: `1.26.3` (for meter type G`)    |
| `MAX_ACTIVE_POWER_DAY_T4`               | `4`  | enable display of maximum daily active power for tariff `T4` - `\|P\|`, OBIS: `15.26.4` (for meter type `R`); `P+`, OBIS: `1.26.4` (for meter type G`)    |
| `MAX_ACTIVE_POWER_MONTH_T1`             | `5`  | enable display of maximum monthly active power for tariff `T1` - `\|P\|`, OBIS: `15.16.1` (for meter type `R`); `P+`, OBIS: `1.16.1` (for meter type `G`) |
| `MAX_ACTIVE_POWER_MONTH_T2`             | `6`  | enable display of maximum monthly active power for tariff `T2` - `\|P\|`, OBIS: `15.16.2` (for meter type `R`); `P+`, OBIS: `1.16.2` (for meter type `G`) |
| `MAX_ACTIVE_POWER_MONTH_T3`             | `7`  | enable display of maximum monthly active power for tariff `T3` - `\|P\|`, OBIS: `15.16.4` (for meter type `R`); `P+`, OBIS: `1.16.3` (for meter type `G`) |
| `MAX_ACTIVE_POWER_MONTH_T4`             | `8`  | enable display of maximum monthly active power for tariff `T4` - `\|P\|`, OBIS: `15.16.4` (for meter type `R`); `P+`, OBIS: `1.16.4` (for meter type `G`) |
| `MAX_REACTIVE_POWER_DAY_T1`             | `9`  | enable display of maximum daily reactive power for tariff `T1` - `Q+`, OBIS: `3.26.1` (for meter type `R`); `QI`, OBIS: `5.26.1` (for meter type `G`)     |
| `MAX_REACTIVE_POWER_DAY_T2`             | `10` | enable display of maximum daily reactive power for tariff `T2` - `Q+`, OBIS: `3.26.2` (for meter type `R`); `QI`, OBIS: `5.26.2` (for meter type `G`)     |
| `MAX_REACTIVE_POWER_DAY_T3`             | `11` | enable display of maximum daily reactive power for tariff `T3` - `Q+`, OBIS: `3.26.3` (for meter type `R`); `QI`, OBIS: `5.26.3` (for meter type `G`)     |
| `MAX_REACTIVE_POWER_DAY_T4`             | `12` | enable display of maximum daily reactive power for tariff `T4` - `Q+`, OBIS: `3.26.4` (for meter type `R`); `QI`, OBIS: `5.26.4` (for meter type `G`)     |
| `MAX_REACTIVE_POWER_MONTH_T1`           | `13` | enable display of maximum monthly reactive power for tariff `T1` - `Q+`, OBIS: `3.16.1` (for meter type `R`); `QI`, OBIS: `5.16.1` (for meter type `G`)   |
| `MAX_REACTIVE_POWER_MONTH_T2`           | `14` | enable display of maximum monthly reactive power for tariff `T2` - `Q+`, OBIS: `3.16.2` (for meter type `R`); `QI`, OBIS: `5.16.2` (for meter type `G`)   |
| `MAX_REACTIVE_POWER_MONTH_T3`           | `15` | enable display of maximum monthly reactive power for tariff `T3` - `Q+`, OBIS: `3.16.3` (for meter type `R`); `QI`, OBIS: `5.16.3` (for meter type `G`)   |
| `MAX_REACTIVE_POWER_MONTH_T4`           | `16` | enable display of maximum monthly reactive power for tariff `T4` - `Q+`, OBIS: `3.16.4` (for meter type `R`); `QI`, OBIS: `5.16.4` (for meter type `G`)   |
| `MAX_NEGATIVE_REACTIVE_POWER_DAY_T1`    | `17` | enable display of maximum daily reactive power for tariff `T1` - `Q-`, OBIS: `4.26.1` (for meter type `R`); `QI`, OBIS: `8.26.1` (for meter type `G`)     |
| `MAX_NEGATIVE_REACTIVE_POWER_DAY_T2`    | `18` | enable display of maximum daily reactive power for tariff `T2` - `Q-`, OBIS: `4.26.2` (for meter type `R`); `QI`, OBIS: `8.26.2` (for meter type `G`)     |
| `MAX_NEGATIVE_REACTIVE_POWER_DAY_T3`    | `19` | enable display of maximum daily reactive power for tariff `T3` - `Q-`, OBIS: `4.26.3` (for meter type `R`); `QI`, OBIS: `8.26.3` (for meter type `G`)     |
| `MAX_NEGATIVE_REACTIVE_POWER_DAY_T4`    | `20` | enable display of maximum daily reactive power for tariff `T4` - `Q-`, OBIS: `4.26.4` (for meter type `R`); `QI`, OBIS: `8.26.4` (for meter type `G`)     |
| `MAX_NEGATIVE_REACTIVE_POWERS_MONTH_T1` | `21` | enable display of maximum monthly reactive power for tariff `T1` - `Q+`, OBIS: `4.16.1` (for meter type `R`); `QI`, OBIS: `8.16.1` (for meter type `G`)   |
| `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T2`  | `22` | enable display of maximum monthly reactive power for tariff `T2` - `Q+`, OBIS: `4.16.2` (for meter type `R`); `QI`, OBIS: `8.16.2` (for meter type `G`)   |
| `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T3`  | `23` | enable display of maximum monthly reactive power for tariff `T3` - `Q+`, OBIS: `4.16.3` (for meter type `R`); `QI`, OBIS: `8.16.3` (for meter type `G`)   |
| `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T4`  | `24` | enable display of maximum monthly reactive power for tariff `T4` - `Q+`, OBIS: `4.16.4` (for meter type `R`); `QI`, OBIS: `8.16.4` (for meter type `G`)   |
| `MAX_EXPORTED_ACTIVE_POWER_DAY_T1`      | `25` | enable display of maximum daily negative active power `P-` for tariff `T1`, OBIS: `2.26.1` (for meter type `G` only)                                      |
| `MAX_EXPORTED_ACTIVE_POWER_DAY_T2`      | `26` | enable display of maximum daily negative active power `P-` for tariff `T2`, OBIS: `2.26.2` (for meter type `G` only)                                      |
| `MAX_EXPORTED_ACTIVE_POWER_DAY_T3`      | `27` | enable display of maximum daily negative active power `P-` for tariff `T3`, OBIS: `2.26.3` (for meter type `G` only)                                      |
| `MAX_EXPORTED_ACTIVE_POWER_DAY_T4`      | `28` | enable display of maximum daily negative active power `P-` for tariff `T4`, OBIS: `2.26.4` (for meter type `G` only)                                      |
| `MAX_EXPORTED_ACTIVE_POWER_MONTH_T1`    | `29` | enable display of maximum monthly negative active power `P-` for tariff `T1`, OBIS: `2.16.1` (for meter type `G` only)                                    |
| `MAX_EXPORTED_ACTIVE_POWER_MONTH_T2`    | `30` | enable display of maximum monthly negative active power `P-` for tariff `T2`, OBIS: `2.16.2` (for meter type `G` only)                                    |
| `MAX_EXPORTED_ACTIVE_POWER_MONTH_T3`    | `31` | enable display of maximum monthly negative active power `P-` for tariff `T3`, OBIS: `2.16.3` (for meter type `G` only)                                    |

#### display settings 4

Bit mask:

| Name                                                | Bit  | Description                                                                                                             |
| --------------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------- |
| `MAXIMUM_EXPORTED_ACTIVE_POWER_MONTH_T4`            | `0`  | enable display of maximum monthly negative active power `P-` for tariff `T4`, OBIS: `2.16.4`, (for meter type `G` only) |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_DAY_T1`            | `1`  | enable display of maximum daily reactive power for tariff `T1`, `Q2`, OBIS: `6.26.1` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_DAY_T2`            | `2`  | enable display of maximum daily reactive power for tariff `T2`, `Q2`, OBIS: `6.26.2` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_DAY_T3`            | `3`  | enable display of maximum daily reactive power for tariff `T3`, `Q2`, OBIS: `6.26.3` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_DAY_T4`            | `4`  | enable display of maximum daily reactive power for tariff `T4`, `Q2`, OBIS: `6.26.4` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_MONTH_T1`          | `5`  | enable display of maximum monthly reactive power for tariff `T1`, `Q2`, OBIS: `6.16.1` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_MONTH_T2`          | `6`  | enable display of maximum monthly reactive power for tariff `T2`, `Q2`, OBIS: `6.16.2` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_MONTH_T3`          | `7`  | enable display of maximum monthly reactive power for tariff `T3`, `Q2`, OBIS: `6.16.3` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_REACTIVE_POWER_MONTH_T4`          | `8`  | enable display of maximum monthly reactive power for tariff `T4`, `Q2`, OBIS: `6.16.4` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_DAY_T1`   | `9`  | enable display of maximum daily reactive power for tariff `T1`, `Q3`, OBIS: `7.26.1` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_DAY_T2`   | `10` | enable display of maximum daily reactive power for tariff `T2`, `Q3`, OBIS: `7.26.2` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_DAY_T3`   | `11` | enable display of maximum daily reactive power for tariff `T3`, `Q3`, OBIS: `7.26.3` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_DAY_T4`   | `12` | enable display of maximum daily reactive power for tariff `T4`, `Q3`, OBIS: `7.26.4` (for meter type `G` only)          |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_MONTH_T1` | `13` | enable display of maximum monthly reactive power for tariff `T1`, `Q3`, OBIS: `7.16.1` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_MONTH_T2` | `14` | enable display of maximum monthly reactive power for tariff `T2`, `Q3`, OBIS: `7.16.2` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_MONTH_T3` | `15` | enable display of maximum monthly reactive power for tariff `T3`, `Q3`, OBIS: `7.16.3` (for meter type `G` only)        |
| `MAXIMUM_EXPORTED_NEGATIVE_REACTIVE_POWER_MONTH_T4` | `16` | enable display of maximum monthly reactive power for tariff `T4`, `Q3`, OBIS: `7.16.4` (for meter type `G` only)        |
| `HOUR_MINUTE_SECOND`                                | `17` | enable time display, OBIS: `0.9.1`                                                                                      |
| `DATE_MONTH_YEAR`                                   | `18` | enable date display, OBIS: `0.9.2`                                                                                      |
| `CURRENT_TRANSFORMER_RATIO`                         | `19` | enable display of current transformer ratio, OBIS: `0.4.2`                                                              |
| `VOLTAGE_TRANSFORMER_RATIO`                         | `20` | enable display of voltage transformer ratio, OBIS: `0.4.2`                                                              |
| `CURRENT_BALANCE`                                   | `21` | enable current balance display                                                                                          |
| `POWER_THRESHOLD_T1`                                | `22` | enable relay off power threshold display for tariff `T1`, OBIS: `5.2.1`                                                 |
| `POWER_THRESHOLD_T2`                                | `23` | enable relay off power threshold display for tariff `T2`, OBIS: `5.2.2`                                                 |
| `POWER_THRESHOLD_T3`                                | `24` | enable relay off power threshold display for tariff `T3`, OBIS: `5.2.3`                                                 |
| `POWER_THRESHOLD_T4`                                | `25` | enable relay off power threshold display for tariff `T4`, OBIS: `5.2.4`                                                 |
| `OPTOPORT_SPEED`                                    | `26` | allows display of current optoport speed (applies only to the additional display)                                       |
| `MAGNET_INDUCTION`                                  | `27` | magnet induction (applies only to the additional display)                                                               |
| `SORT_DISPLAY_SCREENS`                              | `29` | enable display sorting                                                                                                  |
| `TURN_DISPLAY_OFF`                                  | `30` | turn display off                                                                                                        |
| `AUTO_SCREEN_SCROLLING`                             | `31` | enable automatic display scrolling                                                                                      |

#### relay set

Bit mask:

| Name                                | Bit  | Description                                                    |
| ----------------------------------- | ---- | -------------------------------------------------------------- |
| `RELAY_ON_Y`                        | `0`  | relay on function: `1` - enabled, `0` - disabled               |
| `RELAY_ON_CENTER`                   | `1`  | enable by central command                                      |
| `RELAY_ON_PB`                       | `2`  | enable by button                                               |
| `RELAY_ON_TARIFF_1`                 | `3`  | enable by tariff `T1`                                          |
| `RELAY_ON_TARIFF_2`                 | `4`  | enable by tariff `T2`                                          |
| `RELAY_ON_TARIFF_3`                 | `5`  | enable by tariff `T3`                                          |
| `RELAY_ON_TARIFF_4`                 | `6`  | enable by tariff `T4`                                          |
| `RELAY_ON_V_GOOD`                   | `7`  | enable by restoration of good voltage quality                  |
| `RELAY_OFF_Y`                       | `8`  | relay off function: `1` - enabled, `0` - disabled              |
| `RELAY_OFF_CENTER`                  | `9`  | disable by central command                                     |
| `RELAY_OFF_TARIFF_1`                | `10` | disable by tariff `T1`                                         |
| `RELAY_OFF_TARIFF_2`                | `11` | disable by tariff `T2`                                         |
| `RELAY_OFF_TARIFF_3`                | `12` | disable by tariff `T3`                                         |
| `RELAY_OFF_TARIFF_4`                | `13` | disable by tariff `T4`                                         |
| `RELAY_OFF_I_LIMIT`                 | `14` | disable by exceeding load current                              |
| `RELAY_OFF_V_BAD`                   | `15` | disable by poor voltage quality                                |
| `RELAY_OFF_DIFF_CURRENT`            | `16` | turn off when differential current exceeds the allowable limit |
| `RELAY_OFF_ACTIVE_POWER_TARIFF_1`   | `17` | disable by exceeding active power limit for tariff `T1`        |
| `RELAY_OFF_ACTIVE_POWER_TARIFF_2`   | `18` | disable by exceeding active power limit for tariff `T2`        |
| `RELAY_OFF_ACTIVE_POWER_TARIFF_3`   | `19` | disable by exceeding active power limit for tariff `T3`        |
| `RELAY_OFF_ACTIVE_POWER_TARIFF_4`   | `20` | disable by exceeding active power limit for tariff `T4`        |
| `RELAY_OFF_REACTIVE_POWER_TARIFF_1` | `21` | disable by exceeding reactive power imit for tariff `T1`       |
| `RELAY_OFF_REACTIVE_POWER_TARIFF_2` | `22` | disable by exceeding reactive power imit for tariff `T2`       |
| `RELAY_OFF_REACTIVE_POWER_TARIFF_3` | `23` | disable by exceeding reactive power imit for tariff `T3`       |
| `RELAY_OFF_REACTIVE_POWER_TARIFF_4` | `24` | disable by exceeding reactive power limit for tariff `T4`      |
| `RELAY_ON_PF_MIN`                   | `25` | enable by `cos φ`                                              |
| `RELAY_OFF_PF_MIN`                  | `26` | disable by `cos φ`                                             |
| `RELAY_ON_TIMEOUT`                  | `27` | enable after `timeoutRelayOn` timeout                          |
| `RELAY_ON_SALDO`                    | `28` | enable by balance                                              |
| `RELAY_OFF_SALDO`                   | `29` | disable by balance                                             |
| `RELAY_OFF_SALDO_SOFT`              | `30` | disable by balance condition                                   |

#### serial ports set

Bit mask:

| Name                 | Bit    | Description                     |
| -------------------- | ------ | ------------------------------- |
| `PLC_PORT_SPEED`     | `0..3` | `2` - `2400`; `0`, `4` - `9600` |
| `OPTICAL_PORT_SPEED` | `4..7` | `0`, `2` - `2400`; `4` - `9600` |

#### measurement type

Bit mask:

| Name                         | Bit | Description                                                                                                                                                            |
| ---------------------------- | --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `TRANSFORMATION_RATIO`       | `0` | perform measurements using ratio transformation                                                                                                                        |
| `METER_TYPE_R`               | `4` | `R` type meter                                                                                                                                                         |
| `ACCUMULATE_BY_R_PLUS_MINUS` | `7` | reactive energy accumulation type<br>`false` - reactive energy accumulation by quadrants `Q1`, `Q2`, `Q3`, `Q4`<br>`true` - reactive energy accumulation by `R+`, `R-` |

### Examples

<table>
    <thead>
        <tr>
            <th>Field</th>
            <th>Value</th>
            <th>Hex</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>command id</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>command size</td>
            <td><code>95</code></td>
            <td><code>0x5f</code></td>
        </tr>
        <tr>
            <td>maximum voltage threshold, mV</td>
            <td><code>265000</code></td>
            <td><code>0x00040b28</code></td>
        </tr>
        <tr>
            <td>minimum voltage threshold, mV</td>
            <td><code>156000</code></td>
            <td><code>0x00026160</code></td>
        </tr>
        <tr>
            <td>maximum current threshold, mA</td>
            <td><code>120000</code></td>
            <td><code>0x0001d4c0</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T1</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T2</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T3</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T4</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T1</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T2</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T3</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T4</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>power averaging interval, in minutes</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>start date of the monthly billing period</td>
            <td><code>1</code></td>
            <td><code>0x01</code></td>
        </tr>
        <tr>
            <td>display active time</td>
            <td><code>127</code></td>
            <td><code>0x7f</code></td>
        </tr>
        <tr>
            <td>display active time for each screen</td>
            <td><code>7</code></td>
            <td><code>0x07</code></td>
        </tr>
        <tr>
            <td>
                <a href="#display-settings-1">display settings 1</a>
            </td>
            <td>
                <code>SET_ALL_SEGMENT_DISPLAY</code>: <code>true</code><br>
                <code>SOFTWARE_VERSION</code>: <code>false</code><br>
                <code>TOTAL_ACTIVE_ENERGY</code>: <code>true</code><br>
                <code>ACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_REACTIVE_ENERGY</code>: <code>true</code><br>
                <code>REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_NEGATIVE_REACTIVE_ENERGY</code>: <code>true</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_EXPORTED_ACTIVE_ENERGY</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_EXPORTED_REACTIVE_ENERGY</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_EXPORTED_NEGATIVE_REACTIVE_ENERGY</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T4</code>: <code>false</code>
            </td>
            <td><code>0x00001085</code></td>
        </tr>
        <tr>
            <td>
                <a href="#display-settings-2">display settings 2</a>
            </td>
            <td>
                <code>CURRENT_IN_PHASE_A</code>: <code>false</code><br>
                <code>CURRENT_IN_PHASE_B</code>: <code>false</code><br>
                <code>CURRENT_IN_PHASE_C</code>: <code>false</code><br>
                <code>CURRENT_IN_NEUTRAL</code>: <code>false</code><br>
                <code>VOLTAGE_IN_PHASE_A</code>: <code>false</code><br>
                <code>VOLTAGE_IN_PHASE_B</code>: <code>false</code><br>
                <code>VOLTAGE_IN_PHASE_C</code>: <code>false</code><br>
                <code>BATTERY_VOLTAGE</code>: <code>false</code><br>
                <code>FREQUENCY</code>: <code>false</code><br>
                <code>ACTIVE_POWER_SUM</code>: <code>true</code><br>
                <code>ACTIVE_POWER_PHASE_A</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_B</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_C</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_SUM</code>: <code>true</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_A</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_B</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_C</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_SUM</code>: <code>true</code><br>
                <code>REACTIVE_POWER_QMINUS_PHASE_A</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_PHASE_B</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_PHASE_C</code>: <code>false</code><br>
                <code>TOTAL_POWER_FACTOR</code>: <code>false</code><br>
                <code>POWER_FACTOR_PHASE_A</code>: <code>false</code><br>
                <code>POWER_FACTOR_PHASE_B</code>: <code>false</code><br>
                <code>POWER_FACTOR_PHASE_C</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_SUM</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_PHASE_A</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_PHASE_B</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_PHASE_C</code>: <code>false</code><br>
                <code>APPARENT_POWER_QMINUS_SUM</code>: <code>false</code><br>
                <code>APPARENT_POWER_QMINUS_PHASE_A</code>: <code>false</code><br>
                <code>APPARENT_POWER_QMINUS_PHASE_B</code>: <code>false</code>
            </td>
            <td><code>0x00022200</code></td>
        </tr>
        <tr>
            <td>
                <a href="#display-settings-3">display settings 3</a>
            </td>
            <td>
                <code>APPARENT_POWER_QMINUS_PHASE_C</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T3</code>: <code>false</code>
            </td>
            <td><code>0x00000000</code></td>
        </tr>
        <tr>
            <td>
                <a href="#relay-set">relay set</a>
            </td>
            <td>
                <code>RELAY_ON_Y</code>: <code>true</code><br>
                <code>RELAY_ON_CENTER</code>: <code>true</code><br>
                <code>RELAY_ON_PB</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_ON_V_GOOD</code>: <code>false</code><br>
                <code>RELAY_OFF_Y</code>: <code>true</code><br>
                <code>RELAY_OFF_CENTER</code>: <code>true</code><br>
                <code>RELAY_OFF_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_OFF_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_OFF_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_OFF_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_OFF_I_LIMIT</code>: <code>false</code><br>
                <code>RELAY_OFF_V_BAD</code>: <code>false</code><br>
                <code>RELAY_OFF_DIFF_BAD</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_ON_PF_MIN</code>: <code>false</code><br>
                <code>RELAY_OFF_PF_MIN</code>: <code>false</code><br>
                <code>RELAY_ON_TIMEOUT</code>: <code>false</code><br>
                <code>RELAY_ON_SALDO</code>: <code>false</code><br>
                <code>RELAY_OFF_SALDO</code>: <code>false</code><br>
                <code>RELAY_OFF_SALDO_SOFT</code>: <code>false</code>
            </td>
            <td><code>0x00000303</code></td>
        </tr>
        <tr>
            <td>
                <a href="#serial-ports-set">serial ports set</a>
            </td>
            <td>
                <code>plc</code>: <code>9600</code><br>
                <code>optoport</code>: <code>9600</code>
            </td>
            <td><code>0x44</code></td>
        </tr>
        <tr>
            <td>integration period for energy profiles <code>A+</code>, <code>A-</code>, voltage</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>voltage averaging interval to detect voltage quality</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>interval for tracking power off events, in minutes</td>
            <td><code>3</code></td>
            <td><code>0x03</code></td>
        </tr>
        <tr>
            <td>reserved byte</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation due to poor voltage, seconds</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>maximum threshold for the frequency of the grid voltage</td>
            <td><code>55</code></td>
            <td><code>0x37</code></td>
        </tr>
        <tr>
            <td>minimum threshold for the frequency of the grid voltage</td>
            <td><code>45</code></td>
            <td><code>0x2d</code></td>
        </tr>
        <tr>
            <td>year of parameters recording</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>month of parameters recording</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>date of parameters recording</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>the number of digits after the decimal point for displaying energy values</td>
            <td><code>2</code></td>
            <td><code>0x02</code></td>
        </tr>
        <tr>
            <td>numerator of the current transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>denominator of the current transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>numerator of the voltage transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>denominator of the voltage transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>
                <a href="#measurement-type">measurement type</a>
            </td>
            <td>
                <code>TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>METER_TYPE_R</code>: <code>false</code><br>
                <code>ACCUMULATE_BY_R_PLUS_MINUS</code>: <code>false</code>
            </td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>minimum threshold for the <code>cos φ</code> value</td>
            <td><code>0</code></td>
            <td><code>0x0000</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation based on maximum current</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation based on maximum power</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation based on <code>cos φ</code></td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td><code>PMAX</code> settings</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td><a href="#display-settings-4">display settings 4</a>
            <td>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>HOUR_MINUTE_SECOND</code>: <code>true</code><br>
                <code>DATE_MONTH_YEAR</code>: <code>true</code><br>
                <code>CURRENT_TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>VOLTAGE_TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>CURRENT_BALANCE</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T1</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T2</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T3</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T4</code>: <code>false</code><br>
                <code>SORT_DISPLAY_SCREENS</code>: <code>false</code><br>
                <code>AUTO_SCREEN_SCROLLING</code>: <code>true</code>
            </td>
            <td><code>0x80060000</code></td>
        </tr>
    </tbody>
</table>

Command hex dump: `1f 5f 00040b28 00026160 0001d4c0 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 1e 01 7f 07 00001085 00022200 00000000 00000303 44 1e 1e 03 00 05 37 2d 00 00 00 02 0001 0001 0001 0001 00 0000 05 05 05 01 80060000`


## See also

* [Access level](../basics.md#command-access-level)
