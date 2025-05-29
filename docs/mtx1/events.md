# Events

| `ID`   | `Name`                     | `Description`                                                                                                   |
| ------ | -------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `0x01` | `ENERGY_REGISTER_FAULT`    | Accumulative register values lost                                                                               |
| `0x02` | `VENDOR_PAR_FAULT`         | Factory parameter values lost                                                                                   |
| `0x03` | `OP_PAR_FAULT`             | Operator parameter values lost                                                                                  |
| `0x10` | `ACCESS_LOCKED`            | Access closed until end of day due to access key errors                                                         |
| `0x11` | `ERR_ACCESS`               | Invalid access key                                                                                              |
| `0x12` | `CASE_OPEN`                | Meter casing open                                                                                               |
| `0x13` | `CASE_CLOSE`               | Meter casing closed                                                                                             |
| `0x14` | `MAGNETIC_ON`              | Magnetic influence detected                                                                                     |
| `0x15` | `MAGNETIC_OFF`             | Magnetic influence ceased                                                                                       |
| `0x20` | `CHANGE_ACCESS_KEY0`       | Access key level 0 changed                                                                                      |
| `0x21` | `CHANGE_ACCESS_KEY1`       | Access key level 1 changed                                                                                      |
| `0x22` | `CHANGE_ACCESS_KEY2`       | Access key level 2 changed                                                                                      |
| `0x23` | `CHANGE_ACCESS_KEY3`       | Access key level 3 changed                                                                                      |
| `0x24` | `CHANGE_PAR_LOCAL`         | Parameters changed locally                                                                                      |
| `0x25` | `CHANGE_PAR_REMOTE`        | Parameters changed locally (Note: Original text says "locally" for both, might be an error or specific context) |
| `0x26` | `CMD_CHANGE_TIME`          | Time changed (Correction: TIME SET)                                                                             |
| `0x27` | `CMD_RELAY_ON`             | Relay ON command received                                                                                       |
| `0x28` | `CMD_RELAY_OFF`            | Relay OFF command received                                                                                      |
| `0x29` | `CHANGE_COR_TIME`          | Daylight saving time parameters changed                                                                         |
| `0x31` | `ENERGY_REGISTER_OVERFLOW` | Energy accumulation register overflow                                                                           |
| `0x32` | `CHANGE_TARIFF_TABLE`      | Tariff plan changed                                                                                             |
| `0x33` | `SET_TARIFF_TABLE`         | New tariff plan received                                                                                        |
| `0x34` | `SUMMER_TIME`              | Daylight saving time transition                                                                                 |
| `0x35` | `WINTER_TIME`              | Standard time transition                                                                                        |
| `0x36` | `RELAY_ON`                 | Relay ON                                                                                                        |
| `0x37` | `RELAY_OFF`                | Relay OFF                                                                                                       |
| `0x38` | `RESTART`                  | Microcontroller program restart                                                                                 |
| `0x39` | `WD_RESTART`               | WATCHDOG restart                                                                                                |
| `0x3c` | `POWER_B_ON`               | Phase B voltage ON                                                                                              |
| `0x3d` | `POWER_B_OFF`              | Phase B voltage OFF                                                                                             |
| `0x3e` | `POWER_C_ON`               | Phase C voltage ON                                                                                              |
| `0x3f` | `POWER_C_OFF`              | Phase C voltage OFF                                                                                             |
| `0x40` | `V_MAX_OK`                 | Normal voltage restored after over-voltage                                                                      |
| `0x41` | `V_MAX_OVER`               | Voltage above maximum voltage threshold                                                                         |
| `0x42` | `V_MIN_OK`                 | Normal voltage restored after under-voltage                                                                     |
| `0x43` | `V_MIN_OVER`               | Voltage below minimum voltage threshold                                                                         |
| `0x44` | `T_MAX_OK`                 | Normal temperature restored after over-temperature                                                              |
| `0x45` | `T_MAX_OVER`               | Temperature above maximum temperature threshold                                                                 |
| `0x46` | `T_MIN_OK`                 | Normal temperature restored after under-temperature                                                             |
| `0x47` | `T_MIN_OVER`               | Temperature below minimum temperature threshold                                                                 |
| `0x48` | `F_MAX_OK`                 | Normal frequency restored after over-frequency                                                                  |
| `0x49` | `F_MAX_OVER`               | Frequency above maximum grid frequency threshold                                                                |
| `0x4a` | `F_MIN_OK`                 | Normal frequency restored after under-frequency                                                                 |
| `0x4b` | `F_MIN_OVER`               | Frequency below minimum grid frequency threshold                                                                |
| `0x4c` | `I_MAX_OK`                 | Permissible current restored after over-current                                                                 |
| `0x4d` | `I_MAX_OVER`               | Current above maximum current threshold                                                                         |
| `0x4e` | `P_MAX_OK`                 | Permissible power consumption restored after over-power                                                         |
| `0x4f` | `P_MAX_OVER`               | Power consumption above maximum power threshold                                                                 |
| `0x50` | `POWER_SALDO_OK`           | No power excess in credit mode                                                                                  |
| `0x51` | `POWER_SALDO_OVER`         | Power exceeded in credit mode                                                                                   |
| `0x52` | `BATTERY_OK`               | Normal battery voltage restored                                                                                 |
| `0x53` | `BATTERY_FAULT`            | Low battery voltage                                                                                             |
| `0x54` | `CALIBRATION_OK`           | Calibration parameters saved                                                                                    |
| `0x55` | `CALIBRATION_FAULT`        | Calibration parameters lost                                                                                     |
| `0x56` | `CLOCK_OK`                 | Real-time clock normal state restored                                                                           |
| `0x57` | `CLOCK_FAULT`              | Real-time clock not set                                                                                         |
| `0x58` | `POWER_A_OFF`              | Phase A voltage OFF                                                                                             |
| `0x59` | `POWER_A_ON`               | Phase A voltage ON                                                                                              |
| `0x60` | `CMD_RELAY_2_ON`           | Second relay ON command                                                                                         |
| `0x61` | `CMD_RELAY_2_OFF`          | Second relay OFF command                                                                                        |
| `0x62` | `CROSS_ZERO_ENT0`          | Active energy meter transition through `0` for tariff `1` upon reaching `1000000.00` `kW`                       |
| `0x63` | `CROSS_ZERO_ENT1`          | Active energy meter transition through `0` for tariff `2` upon reaching `1000000.00` `kW`                       |
| `0x64` | `CROSS_ZERO_ENT2`          | Active energy meter transition through `0` for tariff `3` upon reaching `1000000.00` `kW`                       |
| `0x65` | `CROSS_ZERO_ENT3`          | Active energy meter transition through `0` for tariff `4` upon reaching `1000000.00` `kW`                       |
| `0x66` | `CALIBRATION_FLAG_SET`     | Calibration flag set                                                                                            |
| `0x67` | `CALIBRATION_FLAG_RESET`   | Calibration flag reset                                                                                          |
| `0x68` | `BAD_TEST_EEPROM`          | EEPROM test failed                                                                                              |
| `0x69` | `BAD_TEST_FRAM`            | FRAM test failed                                                                                                |
| `0x70` | `SET_NEW_SALDO   `         | New prepayment received                                                                                         |
| `0x71` | `SALDO_PARAM_BAD `         | Balance parameters lost                                                                                         |
| `0x72` | `ACC_PARAM_BAD    `        | Accumulation parameters lost                                                                                    |
| `0x73` | `ACC_PARAM_EXT_BAD`        | Additional accumulation parameters lost                                                                         |
| `0x74` | `CALC_PERIOD_BAD `         | Calculation period data lost                                                                                    |
| `0x75` | `BLOCK_TARIFF_BAD `        | Block tariff parameters lost                                                                                    |
| `0x76` | `CALIBRATION_PARAM_BAD`    | Calibration parameter values lost                                                                               |
| `0x77` | `WINTER_SUMMER_BAD`        | Winter/summer time transition parameter values lost                                                             |
| `0x78` | `SALDO_EN_BAD`             | Energy values for balance calculation lost                                                                      |
| `0x79` | `TIME_CORRECT`             | Time correction                                                                                                 |
| `0x7a` | `CASE_KLEMA_OPEN`          | Terminal box open                                                                                               |
| `0x7b` | `CASE_KLEMA_CLOSE`         | Terminal box closed                                                                                             |
| `0x7c` | `CASE_MODULE_OPEN`         | Meter module compartment open                                                                                   |
| `0x7d` | `CASE_MODULE_CLOSE`        | Meter module compartment closed                                                                                 |
| `0x7e` | `POWER_GOOD_DIO`           | POWER_GOOD signal missing                                                                                       |
| `0x90` | `RELAY_HARD_BAD_OFF`       | Relay mechanically switched OFF                                                                                 |
| `0x91` | `RELAY_HARD_ON`            | Relay switched ON after mechanical intervention. Relay state restored.                                          |
| `0x93` | `RELAY_HARD_BAD_ON`        | Relay mechanically switched ON                                                                                  |
| `0x94` | `RELAY_HARD_OFF`           | Relay switched OFF after mechanical intervention. Relay state restored.                                         |
| `0x98` | `CHANGE_TARIFF_TBL_2`      | Tariff plan 2 changed                                                                                           |
| `0x9c` | `SET_SALDO_PARAM`          | Balance parameters set                                                                                          |
| `0x9d` | `POWER_OVER_RELAY_OFF`     | Relay switched OFF due to active power exceeding                                                                |
| `0x9e` | `CROSS_ZERO_EXPORT_ENT0`   | Active energy `A-` meter transition through `0` for tariff `1` upon reaching `1000000.00` `kW`                  |
| `0x9f` | `CROSS_ZERO_EXPORT_ENT1`   | Active energy `A-` meter transition through `0` for tariff `2` upon reaching `1000000.00` `kW`                  |
| `0xa0` | `CROSS_ZERO_EXPORT_ENT2`   | Active energy `A-` meter transition through `0` for tariff `3` upon reaching `1000000.00` `kW`                  |
| `0xa1` | `CROSS_ZERO_EXPORT_ENT3`   | Active energy `A-` meter transition through `0` for tariff `4` upon reaching `1000000.00` `kW`                  |
| `0xa2` | `TIME_CORRECT_NEW`         | Time correction                                                                                                 |
| `0xb0` | `EM_MAGNETIC_ON`           | Electromagnetic influence detected                                                                              |
| `0xb1` | `EM_MAGNETIC_OFF`          | Electromagnetic influence ceased                                                                                |
| `0xb2` | `CURRENT_UNEQUAL_FAULT`    | Current inequality detected                                                                                     |
| `0xb3` | `CURRENT_UNEQUAL_OK`       | Current inequality absent                                                                                       |
| `0xb4` | `BIPOLAR_POWER_FAULT`      | Bipolar power detected in phase and neutral                                                                     |
| `0xb5` | `BIPOLAR_POWER_OK`         | Bipolar power in phase and neutral not detected                                                                 |
| `0xB6` | `RESET_EM_FLAG`            | Electromagnetic influence flag reset                                                                            |
| `0xB7` | `RESET_MAGNET_FLAG`        | Magnetic influence flag reset                                                                                   |
| `0xB9` | `CHANGE_PARAM_CANAL`       | Load profile parameter changed                                                                                  |
| `0xBA` | `RELAY_OFF_BAD_SALDO`      | Relay switched OFF due to consumption limit in credit mode.                                                     |
| `0xE0` | `SET_DEMAND_EN_1MIN`       | `1`-minute energy (voltage) load profiles recording mode set                                                    |
| `0xE1` | `SET_DEMAND_EN_3MIN`       | `3`-minute energy (voltage) load profiles recording mode set                                                    |
| `0xE2` | `SET_DEMAND_EN_5MIN`       | `5`-minute energy (voltage) load profiles recording mode set                                                    |
| `0xE3` | `SET_DEMAND_EN_10MIN`      | `10`-minute energy (voltage) load profiles recording mode set                                                   |
| `0xE4` | `SET_DEMAND_EN_15MIN`      | `15`-minute energy (voltage) load profiles recording mode set                                                   |
| `0xE5` | `SET_DEMAND_EN_30MIN`      | `30`-minute energy (voltage) load profiles recording mode set                                                   |
| `0xE6` | `SET_DEMAND_EN_60MIN`      | `60`-minute energy (voltage) load profiles recording mode set                                                   |
| `0xE7` | `P_MAX_A_MINUS_OK`         | Recovery of permissible generated power `P-` after being too high                                               |
| `0xE8` | `P_MAX_A_MINUS_OVER`       | Generated power `P-` exceeds the maximum power threshold                                                        |
