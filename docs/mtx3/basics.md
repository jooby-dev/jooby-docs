# Basics

## Command access level

The `AccessLevel` field sets one of the 4 access levels.
For each access level the device determines the available set of commands and its encryption key for data encryption.

Available levels:

| ID     | Name          | Description               |
| ------ | ------------- | ------------------------- |
| `0x00` | `UNENCRYPTED` | no encryption is provided |
| `0x01` | `ROOT`        | top security level        |
| `0x02` | `READ_WRITE`  | to set data               |
| `0x03` | `READ_ONLY`   | to get data               |


## Displays

Each device has 4 display sets: `64` main displays and `64` additional displays.

#### Display modes:

| Value | Screen type  | Screen range |
| ----- | ------------ | ------------ |
| `0`   | `main`       | `1..64`      |
| `1`   | `main`       | `65..128`    |
| `2`   | `additional` | `1..64`      |
| `3`   | `additional` | `65..128`    |

A set is a combination of the following displays:

| Number | Name                                            | Description                                                                                                                        |
| ------ | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `1`    | `SET_ALL_SEGMENT_DISPLAY`                       | Test display                                                                                                                       |
| `2`    | `SOFTWARE_VERSION`                              | Display software version                                                                                                           |
| `3`    | `TOTAL_ACTIVE_ENERGY`                           | Total active energy (`A+`) across all tariffs (`1.8.0`)                                                                            |
| `4`    | `ACTIVE_ENERGY_T1`                              | Active energy (`A+`) for tariff `T1` (`1.8.1`)                                                                                     |
| `5`    | `ACTIVE_ENERGY_T2`                              | Active energy (`A+`) for tariff `T2` (`1.8.2`)                                                                                     |
| `6`    | `ACTIVE_ENERGY_T3`                              | Active energy (`A+`) for tariff `T3` (`1.8.3`)                                                                                     |
| `7`    | `ACTIVE_ENERGY_T4`                              | Active energy (`A+`) for tariff `T4` (`1.8.4`)                                                                                     |
| `8`    | `TOTAL_REACTIVE_ENERGY`                         | Total reactive energy (`R+`) across all tariffs (`3.8.0` for `R`-type meters), (`A+R+`, `5.8.0` for `G`-type meters)               |
| `9`    | `REACTIVE_ENERGY_T1`                            | Reactive energy (`R+`) for tariff `T1` (`3.8.1` for `R`-type meters), (`A+R+`, `5.8.1` for `G`-type meters)                        |
| `10`   | `REACTIVE_ENERGY_T2`                            | Reactive energy (`R+`) for tariff `T2` (`3.8.2` for `R`-type meters), (`A+R+`, `5.8.2` for `G`-type meters)                        |
| `11`   | `REACTIVE_ENERGY_T3`                            | Reactive energy (`R+`) for tariff `T3` (`3.8.3` for `R`-type meters), (`A+R+`, `5.8.3` for `G`-type meters)                        |
| `12`   | `REACTIVE_ENERGY_T4`                            | Reactive energy (`R+`) for tariff `T4` (`3.8.4` for `R`-type meters), (`A+R+`, `5.8.4` for `G`-type meters)                        |
| `13`   | `TOTAL_NEGATIVE_REACTIVE_ENERGY`                | Total negative reactive energy (`R-`) across all tariffs (`4.8.0` for `R`-type meters), (`A+R-`, `8.8.0` for `G`-type meters)      |
| `14`   | `NEGATIVE_REACTIVE_ENERGY_T1`                   | Negative reactive energy (`R-`) for tariff `T1` (`4.8.1` for `R`-type meters), (`A+R-`, `8.8.1` for `G`-type meters)               |
| `15`   | `NEGATIVE_REACTIVE_ENERGY_T2`                   | Negative reactive energy (`R-`) for tariff `T2` (`4.8.2` for `R`-type meters), (`A+R-`, `8.8.2` for `G`-type meters)               |
| `16`   | `NEGATIVE_REACTIVE_ENERGY_T3`                   | Negative reactive energy (`R-`) for tariff `T3` (`4.8.3` for `R`-type meters), (`A+R-`, `8.8.3` for `G`-type meters)               |
| `17`   | `NEGATIVE_REACTIVE_ENERGY_T4`                   | Negative reactive energy (`R-`) for tariff `T4` (`4.8.4` for `R`-type meters), (`A+R-`, `8.8.4` for `G`-type meters)               |
| `18`   | `TOTAL_EXPORTED_ACTIVE_ENERGY`                  | Total exported active energy (`A-`) across all tariffs (`2.8.0` for `G`-type meters)                                               |
| `19`   | `EXPORTED_ACTIVE_ENERGY_T1`                     | Exported active energy (`A-`) for tariff `T1` (`2.8.1` for `G`-type meters)                                                        |
| `20`   | `EXPORTED_ACTIVE_ENERGY_T2`                     | Exported active energy (`A-`) for tariff `T2` (`2.8.2` for `G`-type meters)                                                        |
| `21`   | `EXPORTED_ACTIVE_ENERGY_T3`                     | Exported active energy (`A-`) for tariff `T3` (`2.8.3` for `G`-type meters)                                                        |
| `22`   | `EXPORTED_ACTIVE_ENERGY_T4`                     | Exported active energy (`A-`) for tariff `T4` (`2.8.4` for `G`-type meters)                                                        |
| `23`   | `TOTAL_EXPORTED_REACTIVE_ENERGY`                | Total exported reactive energy (`A-R+`) across all tariffs (`6.8.0` for `G`-type meters)                                           |
| `24`   | `EXPORTED_REACTIVE_ENERGY_T1`                   | Exported reactive energy (`A-R+`) for tariff `T1` (`6.8.1` for `G`-type meters)                                                    |
| `25`   | `EXPORTED_REACTIVE_ENERGY_T2`                   | Exported reactive energy (`A-R+`) for tariff `T2` (`6.8.2` for `G`-type meters)                                                    |
| `26`   | `EXPORTED_REACTIVE_ENERGY_T3`                   | Exported reactive energy (`A-R+`) for tariff `T3` (`6.8.3` for `G`-type meters)                                                    |
| `27`   | `EXPORTED_REACTIVE_ENERGY_T4`                   | Exported reactive energy (`A-R+`) for tariff `T4` (`6.8.4` for `G`-type meters)                                                    |
| `28`   | `TOTAL_EXPORTED_NEGATIVE_REACTIVE_ENERGY`       | Total exported negative reactive energy (`A-R-`) across all tariffs (`7.8.0` for `G`-type meters)                                  |
| `29`   | `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T1`          | Exported negative reactive energy (`A-R-`) for tariff `T1` (`7.8.1` for `G`-type meters)                                           |
| `30`   | `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T2`          | Exported negative reactive energy (`A-R-`) for tariff `T2` (`7.8.2` for `G`-type meters)                                           |
| `31`   | `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T3`          | Exported negative reactive energy (`A-R-`) for tariff `T3` (`7.8.3` for `G`-type meters)                                           |
| `32`   | `EXPORTED_NEGATIVE_REACTIVE_ENERGY_T4`          | Exported negative reactive energy (`A-R-`) for tariff `T4` (`7.8.4` for `G`-type meters)                                           |
| `33`   | `CURRENT_IN_PHASE_A`                            | Current in phase `A` (`31.7.0`)                                                                                                    |
| `34`   | `CURRENT_IN_PHASE_B`                            | Current in phase `B` (`51.7.0`)                                                                                                    |
| `35`   | `CURRENT_IN_PHASE_C`                            | Current in phase `C` (`71.7.0`)                                                                                                    |
| `36`   | `CURRENT_IN_NEUTRAL`                            | Current in neutral (`91.7.0`)                                                                                                      |
| `37`   | `VOLTAGE_IN_PHASE_A`                            | Voltage in phase `A` (`32.7.0`)                                                                                                    |
| `38`   | `VOLTAGE_IN_PHASE_B`                            | Voltage in phase `B` (`52.7.0`)                                                                                                    |
| `39`   | `VOLTAGE_IN_PHASE_C`                            | Voltage in phase `C` (`72.7.0`)                                                                                                    |
| `40`   | `BATTERY_VOLTAGE`                               | Battery voltage (`96.6.3`)                                                                                                         |
| `41`   | `FREQUENCY`                                     | Network frequency (`14.7.0`)                                                                                                       |
| `42`   | `ACTIVE_POWER_SUM`                              | Active power of all phases (`P`, `1.7.0` for `R`-type meters), (`±P`, `16.7.0` for `G`-type meters)                                |
| `43`   | `ACTIVE_POWER_PHASE_A`                          | Active power of phase `A` (`P`, `21.7.0` for `R`-type meters), (`±P`, `36.7.0` for `G`-type meters)                                |
| `44`   | `ACTIVE_POWER_PHASE_B`                          | Active power of phase `B` (`P`, `41.7.0` for `R`-type meters), (`±P`, `56.7.0` for `G`-type meters)                                |
| `45`   | `ACTIVE_POWER_PHASE_C`                          | Active power of phase `C` (`P`, `61.7.0` for `R`-type meters), (`±P`, `76.7.0` for `G`-type meters)                                |
| `46`   | `REACTIVE_POWER_QPLUS_SUM`                      | Reactive power of all phases, `Q+` (quadrant `QI + QII`) (`3.7.0`)                                                                 |
| `47`   | `REACTIVE_POWER_QPLUS_PHASE_A`                  | Reactive power of phase `A`, `Q+` (quadrant `QI + QII`) (`23.7.0`)                                                                 |
| `48`   | `REACTIVE_POWER_QPLUS_PHASE_B`                  | Reactive power of phase `B`, `Q+` (quadrant `QI + QII`) (`43.7.0`)                                                                 |
| `49`   | `REACTIVE_POWER_QPLUS_PHASE_C`                  | Reactive power of phase `C`, `Q+` (quadrant `QI + QII`) (`63.7.0`)                                                                 |
| `50`   | `REACTIVE_POWER_QMINUS_SUM`                     | Reactive power of all phases, `Q-` (quadrant `QIII + QIV`) (`4.7.0`)                                                               |
| `51`   | `REACTIVE_POWER_QMINUS_PHASE_A`                 | Reactive power of phase `A`, `Q-` (quadrant `QIII + QIV`) (`24.7.0`)                                                               |
| `52`   | `REACTIVE_POWER_QMINUS_PHASE_B`                 | Reactive power of phase `B`, `Q-` (quadrant `QIII + QIV`) (`44.7.0`)                                                               |
| `53`   | `REACTIVE_POWER_QMINUS_PHASE_C`                 | Reactive power of phase `C`, `Q-` (quadrant `QIII + QIV`) (`64.7.0`)                                                               |
| `54`   | `TOTAL_POWER_FACTOR`                            | Total power factor (`cos φ`) (`13.7.0`)                                                                                            |
| `55`   | `POWER_FACTOR_PHASE_A`                          | Power factor (`cos φ`) of phase `A` (`33.7.0`)                                                                                     |
| `56`   | `POWER_FACTOR_PHASE_B`                          | Power factor (`cos φ`) of phase `B` (`53.7.0`)                                                                                     |
| `57`   | `POWER_FACTOR_PHASE_C`                          | Power factor (`cos φ`) of phase `C` (`73.7.0`)                                                                                     |
| `58`   | `APPARENT_POWER_QPLUS_SUM`                      | Total apparent power `S+` (quadrant `QI + QIV`) (`9.7.0`)                                                                          |
| `59`   | `APPARENT_POWER_QPLUS_PHASE_A`                  | Apparent power `S+` of phase `A` (quadrant `QI + QIV`) (`29.7.0`)                                                                  |
| `60`   | `APPARENT_POWER_QPLUS_PHASE_B`                  | Apparent power `S+` of phase `B` (quadrant `QI + QIV`) (`49.7.0`)                                                                  |
| `61`   | `APPARENT_POWER_QPLUS_PHASE_C`                  | Apparent power `S+` of phase `C` (quadrant `QI + QIV`) (`69.7.0`)                                                                  |
| `62`   | `APPARENT_POWER_QMINUS_SUM`                     | Total apparent power `S-` (quadrant `QII + QIII`) (`10.7.0`)                                                                       |
| `63`   | `APPARENT_POWER_QMINUS_PHASE_A`                 | Apparent power `S-` of phase `A` (quadrant `QII + QIII`) (`30.7.0`)                                                                |
| `64`   | `APPARENT_POWER_QMINUS_PHASE_B`                 | Apparent power `S-` of phase `B` (quadrant `QII + QIII`) (`50.7.0`)                                                                |
| `65`   | `APPARENT_POWER_QMINUS_PHASE_C`                 | Apparent power `S-` of phase `C`, (quadrant `QII + QIII`) (`70.7.0`)                                                               |
| `66`   | `MAX_ACTIVE_POWER_DAY_T1`                       | Maximum daily active power for tariff `T1` (`                                                                                      | P | `, `15.26.1` for `R`-type meters), (`P+`, `1.26.1` for `G`-type meters) |
| `67`   | `MAX_ACTIVE_POWER_DAY_T2`                       | Maximum daily active power for tariff `T2` (`                                                                                      | P | `, `15.26.2` for `R`-type meters), (`P+`, `1.26.2` for `G`-type meters) |
| `68`   | `MAX_ACTIVE_POWER_DAY_T3`                       | Maximum daily active power for tariff `T3` (`                                                                                      | P | `, `15.26.3` for `R`-type meters), (`P+`, `1.26.3` for `G`-type meters) |
| `69`   | `MAX_ACTIVE_POWER_DAY_T4`                       | Maximum daily active power for tariff `T4` (`                                                                                      | P | `, `15.26.4` for `R`-type meters), (`P+`, `1.26.4` for `G`-type meters) |
| `70`   | `MAX_ACTIVE_POWER_MONTH_T1`                     | Maximum monthly active power for tariff `T1` (`                                                                                    | P | `, `15.16.1` for `R`-type meters), (`P+`, `1.16.1` for `G`-type meters) |
| `71`   | `MAX_ACTIVE_POWER_MONTH_T2`                     | Maximum monthly active power for tariff `T2` (`                                                                                    | P | `, `15.16.2` for `R`-type meters), (`P+`, `1.16.2` for `G`-type meters) |
| `72`   | `MAX_ACTIVE_POWER_MONTH_T3`                     | Maximum monthly active power for tariff `T3` (`                                                                                    | P | `, `15.16.3` for `R`-type meters), (`P+`, `1.16.3` for `G`-type meters) |
| `73`   | `MAX_ACTIVE_POWER_MONTH_T4`                     | Maximum monthly active power for tariff `T4` (`                                                                                    | P | `, `15.16.4` for `R`-type meters), (`P+`, `1.16.4` for `G`-type meters) |
| `74`   | `MAX_REACTIVE_POWER_DAY_T1`                     | Maximum daily reactive power for tariff `T1` (`Q+`, `3.26.1` for `R`-type meters), (`Q1`, `5.26.1` for `G`-type meters)            |
| `75`   | `MAX_REACTIVE_POWER_DAY_T2`                     | Maximum daily reactive power for tariff `T2` (`Q+`, `3.26.2` for `R`-type meters), (`Q1`, `5.26.2` for `G`-type meters)            |
| `76`   | `MAX_REACTIVE_POWER_DAY_T3`                     | Maximum daily reactive power for tariff `T3` (`Q+`, `3.26.3` for `R`-type meters), (`Q1`, `5.26.3` for `G`-type meters)            |
| `77`   | `MAX_REACTIVE_POWER_DAY_T4`                     | Maximum daily reactive power for tariff `T4` (`Q+`, `3.26.4` for `R`-type meters), (`Q1`, `5.26.4` for `G`-type meters)            |
| `78`   | `MAX_REACTIVE_POWER_MONTH_T1`                   | Maximum monthly reactive power for tariff `T1` (`Q+`, `3.16.1` for `R`-type meters), (`Q1`, `5.16.1` for `G`-type meters)          |
| `79`   | `MAX_REACTIVE_POWER_MONTH_T2`                   | Maximum monthly reactive power for tariff `T2` (`Q+`, `3.16.2` for `R`-type meters), (`Q1`, `5.16.2` for `G`-type meters)          |
| `80`   | `MAX_REACTIVE_POWER_MONTH_T3`                   | Maximum monthly reactive power for tariff `T3` (`Q+`, `3.16.3` for `R`-type meters), (`Q1`, `5.16.3` for `G`-type meters)          |
| `81`   | `MAX_REACTIVE_POWER_MONTH_T4`                   | Maximum monthly reactive power for tariff `T4` (`Q+`, `3.16.4` for `R`-type meters), (`Q1`, `5.16.4` for `G`-type meters)          |
| `82`   | `MAX_NEGATIVE_REACTIVE_POWER_DAY_T1`            | Maximum daily negative reactive power for tariff `T1` (`Q-`, `4.26.1` for `R`-type meters), (`Q4`, `8.26.1` for `G`-type meters)   |
| `83`   | `MAX_NEGATIVE_REACTIVE_POWER_DAY_T2`            | Maximum daily negative reactive power for tariff `T2` (`Q-`, `4.26.2` for `R`-type meters), (`Q4`, `8.26.2` for `G`-type meters)   |
| `84`   | `MAX_NEGATIVE_REACTIVE_POWER_DAY_T3`            | Maximum daily negative reactive power for tariff `T3` (`Q-`, `4.26.3` for `R`-type meters), (`Q4`, `8.26.3` for `G`-type meters)   |
| `85`   | `MAX_NEGATIVE_REACTIVE_POWER_DAY_T4`            | Maximum daily negative reactive power for tariff `T4` (`Q-`, `4.26.4` for `R`-type meters), (`Q4`, `8.26.4` for `G`-type meters)   |
| `86`   | `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T1`          | Maximum monthly negative reactive power for tariff `T1` (`Q-`, `4.16.1` for `R`-type meters), (`Q4`, `8.16.1` for `G`-type meters) |
| `87`   | `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T2`          | Maximum monthly negative reactive power for tariff `T2` (`Q-`, `4.16.2` for `R`-type meters), (`Q4`, `8.16.2` for `G`-type meters) |
| `88`   | `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T3`          | Maximum monthly negative reactive power for tariff `T3` (`Q-`, `4.16.3` for `R`-type meters), (`Q4`, `8.16.3` for `G`-type meters) |
| `89`   | `MAX_NEGATIVE_REACTIVE_POWER_MONTH_T4`          | Maximum monthly negative reactive power for tariff `T4` (`Q-`, `4.16.4` for `R`-type meters), (`Q4`, `8.16.4` for `G`-type meters) |
| `90`   | `MAX_EXPORTED_ACTIVE_POWER_DAY_T1`              | Maximum daily exported active power for tariff `T1` (`P-`, `2.26.1` for `G`-type meters)                                           |
| `91`   | `MAX_EXPORTED_ACTIVE_POWER_DAY_T2`              | Maximum daily exported active power for tariff `T2` (`P-`, `2.26.2` for `G`-type meters)                                           |
| `92`   | `MAX_EXPORTED_ACTIVE_POWER_DAY_T3`              | Maximum daily exported active power for tariff `T3` (`P-`, `2.26.3` for `G`-type meters)                                           |
| `93`   | `MAX_EXPORTED_ACTIVE_POWER_DAY_T4`              | Maximum daily exported active power for tariff `T4` (`P-`, `2.26.4` for `G`-type meters)                                           |
| `94`   | `MAX_EXPORTED_ACTIVE_POWER_MONTH_T1`            | Maximum monthly exported active power for tariff `T1` (`P-`, `2.16.1` for `G`-type meters)                                         |
| `95`   | `MAX_EXPORTED_ACTIVE_POWER_MONTH_T2`            | Maximum monthly exported active power for tariff `T2` (`P-`, `2.16.2` for `G`-type meters)                                         |
| `96`   | `MAX_EXPORTED_ACTIVE_POWER_MONTH_T3`            | Maximum monthly exported active power for tariff `T3` (`P-`, `2.16.3` for `G`-type meters)                                         |
| `97`   | `MAX_EXPORTED_ACTIVE_POWER_MONTH_T4`            | Maximum monthly active power for tariff `T4` (`P-`, `2.16.4` for `G`-type meters)                                                  |
| `98`   | `MAX_EXPORTED_REACTIVE_POWER_DAY_T1`            | Maximum daily exported reactive power for tariff `T1` (`Q2`, `6.26.1` for `G`-type meters)                                         |
| `99`   | `MAX_EXPORTED_REACTIVE_POWER_DAY_T2`            | Maximum daily exported reactive power for tariff `T2` (`Q2`, `6.26.2` for `G`-type meters)                                         |
| `100`  | `MAX_EXPORTED_REACTIVE_POWER_DAY_T3`            | Maximum daily exported reactive power for tariff `T3` (`Q2`, `6.26.3` for `G`-type meters)                                         |
| `101`  | `MAX_EXPORTED_REACTIVE_POWER_DAY_T4`            | Maximum daily exported reactive power for tariff `T4` (`Q2`, `6.26.4` for `G`-type meters)                                         |
| `102`  | `MAX_EXPORTED_REACTIVE_POWER_MONTH_T1`          | Maximum monthly exported reactive power for tariff `T1` (`Q2`, `6.16.1` for `G`-type meters)                                       |
| `103`  | `MAX_EXPORTED_REACTIVE_POWER_MONTH_T2`          | Maximum monthly exported reactive power for tariff `T2` (`Q2`, `6.16.2` for `G`-type meters)                                       |
| `104`  | `MAX_EXPORTED_REACTIVE_POWER_MONTH_T3`          | Maximum monthly exported reactive power for tariff `T3` (`Q2`, `6.16.3` for `G`-type meters)                                       |
| `105`  | `MAX_EXPORTED_REACTIVE_POWER_MONTH_T4`          | Maximum monthly exported reactive power for tariff `T4` (`Q2`, `6.16.4` for `G`-type meters)                                       |
| `106`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T1`   | Maximum daily negative exported reactive power for tariff `T1` (`Q3`, `7.26.1` for `G`-type meters)                                |
| `107`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T2`   | Maximum daily negative exported reactive power for tariff `T2` (`Q3`, `7.26.2` for `G`-type meters)                                |
| `108`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T3`   | Maximum daily negative exported reactive power for tariff `T3` (`Q3`, `7.26.3` for `G`-type meters)                                |
| `109`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T4`   | Maximum daily negative exported reactive power for tariff `T4` (`Q3`, `7.26.4` for `G`-type meters)                                |
| `110`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T1` | Maximum monthly negative exported reactive power for tariff `T1` (`Q3`, `7.16.1` for `G`-type meters)                              |
| `111`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T2` | Maximum monthly negative exported reactive power for tariff `T2` (`Q3`, `7.16.2` for `G`-type meters)                              |
| `112`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T3` | Maximum monthly negative exported reactive power for tariff `T3` (`Q3`, `7.16.3` for `G`-type meters)                              |
| `113`  | `MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T4` | Maximum monthly negative exported reactive power for tariff `T4` (`Q3`, `7.16.4` for `G`-type meters)                              |
| `114`  | `HOUR_MINUTE_SECOND`                            | Current time of the meter clock (`0.9.1`)                                                                                          |
| `115`  | `DATE_MONTH_YEAR`                               | Current date of the meter clock (`0.9.2`)                                                                                          |
| `116`  | `CURRENT_TRANSFORMATION_RATIO`                  | Current transformer ratio (`0.4.2`)                                                                                                |
| `117`  | `VOLTAGE_TRANSFORMATION_RATIO`                  | Voltage transformer ratio (`0.4.3`)                                                                                                |
| `118`  | `CURRENT_BALANCE`                               | Display current balance                                                                                                            |
| `119`  | `POWER_THRESHOLD_T1`                            | Display power threshold for tariff `T1` (`5.2.1`), since build `302.35.005`                                                        |
| `120`  | `POWER_THRESHOLD_T2`                            | Display power threshold for tariff `T2` (`5.2.2`)                                                                                  |
| `121`  | `POWER_THRESHOLD_T3`                            | Display power threshold for tariff `T3` (`5.2.3`)                                                                                  |
| `122`  | `POWER_THRESHOLD_T4`                            | Display power threshold for tariff `T4` (`5.2.4`)                                                                                  |
| `123`  | `OPTOPORT_SPEED`                                | Optical port speed (for additional display only)                                                                                   |
| `124`  | `MAGNET_INDUCTION`                              | Magnetic induction (for additional display only)                                                                                   |
