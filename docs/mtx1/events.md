# Events

| `ID`   | `Name`                         | `Description`                                                                                 |
|--------|--------------------------------|-----------------------------------------------------------------------------------------------|
| `0x01` | `ENERGY_REGISTER_FAULT`        | Accumulative register values lost.                                                            |
| `0x02` | `VENDOR_PAR_FAULT`             | Factory parameter values lost.                                                                |
| `0x03` | `OP_PARAMETERS_VALUES_FAULT`   | Operator parameter values lost.                                                               |
| `0x10` | `ACCESS_LOCKED`                | Access locked until end of day due to key access errors.                                      |
| `0x11` | `ACCESS_ERROR`                 | Invalid access key.                                                                           |
| `0x12` | `CASE_OPENED`                  | Meter case opened.                                                                            |
| `0x13` | `CASE_CLOSED`                  | Meter case closed.                                                                            |
| `0x14` | `MAGNETIC_INFLUENCE_ON`        | Magnetic influence detected.                                                                  |
| `0x15` | `MAGNETIC_INFLUENCE_OFF`       | Magnetic influence ceased.                                                                    |
| `0x20` | `CHANGE_ACCESS_KEY0`           | Access key level `0` changed.                                                                 |
| `0x21` | `CHANGE_ACCESS_KEY1`           | Access key level `1` changed.                                                                 |
| `0x22` | `CHANGE_ACCESS_KEY2`           | Access key level `2` changed.                                                                 |
| `0x23` | `CHANGE_ACCESS_KEY3`           | Access key level `3` changed.                                                                 |
| `0x24` | `CHANGE_PARAMETERS_LOCAL`      | Parameters changed locally.                                                                   |
| `0x25` | `CHANGE_PARAMETERS_REMOTE`     | Parameters changed remotely.                                                                  |
| `0x26` | `CMD_CHANGE_TIME`              | Time changed (Correction: TIME SET).                                                          |
| `0x27` | `CMD_RELAY_ON`                 | `Relay on` command received.                                                                  |
| `0x28` | `CMD_RELAY_OFF`                | `Relay off` command received.                                                                 |
| `0x29` | `CHANGE_COR_TIME`              | Daylight saving time transition parameters changed.                                           |
| `0x31` | `ENERGY_REGISTER_OVERFLOW`     | Energy accumulation register overflow.                                                        |
| `0x32` | `CHANGE_TARIFF_TABLE`          | Tariff plan changed.                                                                          |
| `0x33` | `SET_TARIFF_TABLE`             | New tariff plan received.                                                                     |
| `0x34` | `SUMMER_TIME`                  | Switched to summer time.                                                                      |
| `0x35` | `WINTER_TIME`                  | Switched to winter time.                                                                      |
| `0x36` | `RELAY_ON`                     | Relay turned on.                                                                              |
| `0x37` | `RELAY_OFF`                    | Relay turned off.                                                                             |
| `0x38` | `RESTART`                      | Microcontroller program restart.                                                              |
| `0x39` | `WD_RESTART`                   | WATCHDOG restart.                                                                             |
| `0x3C` | `POWER_B_ON`                   | Phase `B` voltage turned on.                                                                  |
| `0x3D` | `POWER_B_OFF`                  | Phase `B` voltage turned off.                                                                 |
| `0x3E` | `POWER_C_ON`                   | Phase `C` voltage turned on.                                                                  |
| `0x3F` | `POWER_C_OFF`                  | Phase `C` voltage turned off.                                                                 |
| `0x40` | `V_MAX_OK`                     | Normal voltage restored after over-voltage.                                                   |
| `0x41` | `V_MAX_OVER`                   | Voltage above maximum voltage threshold.                                                      |
| `0x42` | `V_MIN_OK`                     | Normal voltage restored after under-voltage.                                                  |
| `0x43` | `V_MIN_OVER`                   | Voltage below minimum voltage threshold.                                                      |
| `0x44` | `T_MAX_OK`                     | Normal temperature restored after over-temperature.                                           |
| `0x45` | `T_MAX_OVER`                   | Temperature above maximum temperature threshold.                                              |
| `0x46` | `T_MIN_OK`                     | Normal temperature restored after under-temperature.                                          |
| `0x47` | `T_MIN_OVER`                   | Temperature below minimum temperature threshold.                                              |
| `0x48` | `F_MAX_OK`                     | Normal frequency restored after over-frequency.                                               |
| `0x49` | `F_MAX_OVER`                   | Frequency above maximum grid frequency threshold.                                             |
| `0x4A` | `F_MIN_OK`                     | Normal frequency restored after under-frequency.                                              |
| `0x4B` | `F_MIN_OVER`                   | Frequency below minimum grid frequency threshold.                                             |
| `0x4C` | `I_MAX_OK`                     | Permissible current restored after over-current.                                              |
| `0x4D` | `I_MAX_OVER`                   | Current above maximum current threshold.                                                      |
| `0x4E` | `P_MAX_OK`                     | Permissible power consumption restored after over-power.                                      |
| `0x4F` | `P_MAX_OVER`                   | Power consumption above maximum power threshold.                                              |
| `0x50` | `POWER_SALDO_OK`               | No power excess in credit mode.                                                               |
| `0x51` | `POWER_SALDO_OVER`             | Power exceeded in credit mode.                                                                |
| `0x52` | `BATTERY_OK`                   | Normal battery voltage restored.                                                              |
| `0x53` | `BATTERY_FAULT`                | Low battery voltage.                                                                          |
| `0x54` | `CALIBRATION_OK`               | Calibration parameters set.                                                                   |
| `0x55` | `CALIBRATION_FAULT`            | Calibration parameters lost.                                                                  |
| `0x56` | `CLOCK_OK`                     | Real-time clock normal state restored.                                                        |
| `0x57` | `CLOCK_FAULT`                  | Real-time clock not set.                                                                      |
| `0x58` | `POWER_A_OFF`                  | Phase `A` voltage turned off.                                                                 |
| `0x59` | `POWER_A_ON`                   | Phase `A` voltage turned on.                                                                  |
| `0x60` | `CMD_RELAY_2_ON`               | Second relay ON command.                                                                      |
| `0x61` | `CMD_RELAY_2_OFF`              | Second relay OFF command.                                                                     |
| `0x62` | `CROSS_ZERO_EN_T1`             | Active energy meter transition through `0` for tariff `1` upon reaching `1000000.00` kW.      |
| `0x63` | `CROSS_ZERO_EN_T2`             | Active energy meter transition through `0` for tariff `2` upon reaching `1000000.00` kW.      |
| `0x64` | `CROSS_ZERO_EN_T3`             | Active energy meter transition through `0` for tariff `3` upon reaching `1000000.00` kW.      |
| `0x65` | `CROSS_ZERO_EN_T4`             | Active energy meter transition through `0` for tariff `4` upon reaching `1000000.00` kW.      |
| `0x66` | `CALIBRATION_FLAG_SET`         | Calibration flag set.                                                                         |
| `0x67` | `CALIBRATION_FLAG_RESET`       | Calibration flag reset.                                                                       |
| `0x68` | `BAD_TEST_EEPROM`              | EEPROM test failed.                                                                           |
| `0x69` | `BAD_TEST_FRAM`                | FRAM test failed.                                                                             |
| `0x70` | `SET_NEW_SALDO`                | New prepayment received.                                                                      |
| `0x71` | `SALDO_PARAMETERS_FAULT`       | Balance parameters lost.                                                                      |
| `0x72` | `ACC_PARAMETERS_FAULT`         | Accumulation parameters lost.                                                                 |
| `0x73` | `ACC_PARAMETERS_EXT_FAULT`     | Additional accumulation parameters lost.                                                      |
| `0x74` | `CALC_PERIOD_FAULT`            | Calculation period data lost.                                                                 |
| `0x75` | `BLOCK_TARIFF_FAULT`           | Block tariff parameters lost.                                                                 |
| `0x76` | `CALIBRATION_PARAMETERS_FAULT` | Calibration parameter values lost.                                                            |
| `0x77` | `WINTER_SUMMER_FAULT`          | Winter/summer time transition parameter values lost.                                          |
| `0x78` | `SALDO_EN_FAULT`               | Energy values for balance calculation lost.                                                   |
| `0x79` | `TIME_CORRECT`                 | Time correction.                                                                              |
| `0x7A` | `CASE_TERMINAL_BOX_OPENED`     | Terminal box opened.                                                                          |
| `0x7B` | `CASE_TERMINAL_BOX_CLOSED`     | Terminal box closed.                                                                          |
| `0x7C` | `CASE_MODULE_OPENED`           | Meter module compartment opened.                                                              |
| `0x7D` | `CASE_MODULE_CLOSED`           | Meter module compartment closed.                                                              |
| `0x7E` | `POWER_GOOD_DIO`               | POWER_GOOD signal missing.                                                                    |
| `0x90` | `RELAY_HARD_BAD_OFF`           | Relay mechanically switched OFF.                                                              |
| `0x91` | `RELAY_HARD_ON`                | Relay switched ON after mechanical intervention. Relay state restored.                        |
| `0x93` | `RELAY_HARD_BAD_ON`            | Relay mechanically switched ON.                                                               |
| `0x94` | `RELAY_HARD_OFF`               | Relay switched OFF after mechanical intervention. Relay state restored.                       |
| `0x98` | `CHANGE_TARIFF_TABLE_2`        | Tariff plan `2` changed.                                                                      |
| `0x9C` | `SET_SALDO_PARAM`              | Balance parameters set.                                                                       |
| `0x9D` | `POWER_OVER_RELAY_OFF`         | Relay switched OFF due to active power exceeding.                                             |
| `0x9E` | `CROSS_ZERO_EXPORT_EN_T1`      | Active energy `A-` meter transition through `0` for tariff `1` upon reaching `1000000.00` kW. |
| `0x9F` | `CROSS_ZERO_EXPORT_EN_T2`      | Active energy `A-` meter transition through `0` for tariff `2` upon reaching `1000000.00` kW. |
| `0xA0` | `CROSS_ZERO_EXPORT_EN_T3`      | Active energy `A-` meter transition through `0` for tariff `3` upon reaching `1000000.00` kW. |
| `0xA1` | `CROSS_ZERO_EXPORT_EN_T4`      | Active energy `A-` meter transition through `0` for tariff `4` upon reaching `1000000.00` kW. |
| `0xA2` | `TIME_CORRECT_NEW`             | Time correction. Reserved event - do not use.                                                 |
| `0xB0` | `EM_MAGNETIC_INFLUENCE_ON`     | Electromagnetic influence detected.                                                           |
| `0xB1` | `EM_MAGNETIC_INFLUENCE_OFF`    | Electromagnetic influence ceased.                                                             |
| `0xB2` | `CURRENT_UNEQUAL_FAULT`        | Current inequality detected.                                                                  |
| `0xB3` | `CURRENT_UNEQUAL_OK`           | Current inequality absent.                                                                    |
| `0xB4` | `BIPOLAR_POWER_FAULT`          | Bipolar power detected in phase and neutral.                                                  |
| `0xB5` | `BIPOLAR_POWER_OK`             | Bipolar power in phase and neutral not detected.                                              |
| `0xB6` | `RESET_EM_FLAG`                | Electromagnetic influence flag reset.                                                         |
| `0xB7` | `RESET_MAGNET_FLAG`            | Magnetic influence flag reset.                                                                |
| `0xB9` | `CHANGE_PARAMETERS_CHANNEL`    | Load profile parameter changed.                                                               |
| `0xBA` | `RELAY_OFF_BAD_SALDO`          | Relay switched OFF due to consumption limit in credit mode.                                   |
| `0xE0` | `SET_DEMAND_EN_1MIN`           | `1`-minute energy (voltage) load profiles recording mode set.                                 |
| `0xE1` | `SET_DEMAND_EN_3MIN`           | `3`-minute energy (voltage) load profiles recording mode set.                                 |
| `0xE2` | `SET_DEMAND_EN_5MIN`           | `5`-minute energy (voltage) load profiles recording mode set.                                 |
| `0xE3` | `SET_DEMAND_EN_10MIN`          | `10`-minute energy (voltage) load profiles recording mode set.                                |
| `0xE4` | `SET_DEMAND_EN_15MIN`          | `15`-minute energy (voltage) load profiles recording mode set.                                |
| `0xE5` | `SET_DEMAND_EN_30MIN`          | `30`-minute energy (voltage) load profiles recording mode set.                                |
| `0xE6` | `SET_DEMAND_EN_60MIN`          | `60`-minute energy (voltage) load profiles recording mode set.                                |
| `0xE7` | `P_MAX_A_MINUS_OK`             | Recovery of permissible generated power `P-` after being too high.                            |
| `0xE8` | `P_MAX_A_MINUS_OVER`           | Generated power `P-` exceeds the maximum power threshold.                                     |
