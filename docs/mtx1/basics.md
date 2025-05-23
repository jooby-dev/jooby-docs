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

Each device has 2 display sets: `32` main displays and `32` additional displays.

Display modes:

| Value | Screen type  | Screen range |
| ----- | ------------ | ------------ |
| `0`   | `main`       | `1..32`      |
| `1`   | `additional` | `1..32`      |

A set is a combination of the following displays:

| Number | Name                           | Description                                                 |
| ------ | ------------------------------ | ----------------------------------------------------------- |
| `1`    | `SET_ALL_SEGMENT_DISPLAY`      | Display test                                                |
| `2`    | `SOFTWARE_VERSION`             | Software version (0.2.0)                                    |
| `3`    | `TOTAL_ACTIVE_ENERGY`          | Total active energy A+ (1.8.0)                              |
| `4`    | `ACTIVE_ENERGY_T1`             | Active energy A+, T1 (1.8.1)                                |
| `5`    | `ACTIVE_ENERGY_T2`             | Active energy A+, T2 (1.8.2)                                |
| `6`    | `ACTIVE_ENERGY_T3`             | Active energy A+, T3 (1.8.3)                                |
| `7`    | `ACTIVE_ENERGY_T4`             | Active energy A+, T4 (1.8.4)                                |
| `8`    | `ACTIVE_POWER_PER_PHASE`       | Active power consumption per phase (21.7.0)                 |
| `9`    | `ACTIVE_POWER_IN_NEUTRAL`      | Active power consumption in neutral (41.7.0)                |
| `10`   | `CURRENT_IN_PHASE`             | Phase current (31.7.0)                                      |
| `11`   | `CURRENT_IN_NEUTRAL`           | Current in neutral (51.7.0)                                 |
| `12`   | `VOLTAGE`                      | Voltage (32.7.0)                                            |
| `13`   | `HOUR_MINUTE_SECOND`           | Time (0.9.1)                                                |
| `14`   | `DATE_MONTH_YEAR`              | Date (0.9.2)                                                |
| `15`   | `TOTAL_EXPORTED_ACTIVE_ENERGY` | Total active energy A- (2.8.0)                              |
| `16`   | `EXPORTED_ACTIVE_ENERGY_T1`    | Active energy A-, T1 (2.8.1)                                |
| `17`   | `EXPORTED_ACTIVE_ENERGY_T2`    | Active energy A-, T2 (2.8.2)                                |
| `18`   | `EXPORTED_ACTIVE_ENERGY_T3`    | Active energy A-, T3 (2.8.3)                                |
| `19`   | `EXPORTED_ACTIVE_ENERGY_T4`    | Active energy A-, T4 (2.8.4)                                |
| `20`   | `POWER_COEFFICIENT_PHASE_A`    | Power ratio (cos φ) in channel A (33.7.0)                   |
| `21`   | `POWER_COEFFICIENT_PHASE_B`    | Power ratio (cos φ) in channel B (53.7.0)                   |
| `22`   | `BATTERY_VOLTAGE`              | Battery voltage (96.6.3)                                    |
| `23`   | `POWER_THRESHOLD_T1`           | Relay cut-off power threshold according to tariff 1 (5.2.1) |
| `24`   | `POWER_THRESHOLD_T2`           | Relay cut-off power threshold according to tariff 2 (5.2.2) |
| `25`   | `POWER_THRESHOLD_T3`           | Relay cut-off power threshold according to tariff 3 (5.2.3) |
| `26`   | `POWER_THRESHOLD_T4`           | Relay cut-off power threshold according to tariff 4 (5.2.4) |
| `28`   | `MAGNET_INDUCTION`             | Magnet induction                                            |
| `30`   | `CURRENT_BALANCE`              | Current balance (saldo)                                     |
| `31`   | `OPTOPORT_SPEED`               | Allow display of current optoport speed (104.21.017)        |
