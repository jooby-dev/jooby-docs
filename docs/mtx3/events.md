# Events

| `ID`   | `Name`                                 | `Indication code` | `Description`                                                                           |
|--------|----------------------------------------|-------------------|-----------------------------------------------------------------------------------------|
| `0x01` | `ENERGY_T1_FAULT`                      | `C.001`           | Tariff `1` cumulative register values lost.                                             |
| `0x02` | `ENERGY_T2_FAULT`                      | `C.002`           | Tariff `2` cumulative register values lost.                                             |
| `0x03` | `ENERGY_T3_FAULT`                      | `C.003`           | Tariff `3` cumulative register values lost.                                             |
| `0x04` | `ENERGY_T4_FAULT`                      | `C.004`           | Tariff `4` cumulative register values lost.                                             |
| `0x11` | `ACCESS_LOCKED`                        | `C.017`           | Access locked until end of day due to key access errors.                                |
| `0x12` | `ACCESS_UNLOCKED`                      | `C.018`           | Access unlocked.                                                                        |
| `0x13` | `ACCESS_ERROR`                         | `C.019`           | Invalid access key.                                                                     |
| `0x14` | `CASE_OPENED`                          | `C.020`           | Meter case opened.                                                                      |
| `0x15` | `CASE_CLOSED`                          | `C.021`           | Meter case closed.                                                                      |
| `0x16` | `MAGNETIC_INFLUENCE_ON`                | `C.022`           | Magnetic influence detected.                                                            |
| `0x17` | `MAGNETIC_INFLUENCE_OFF`               | `C.023`           | Magnetic influence ceased.                                                              |
| `0x20` | `CHANGE_ACCESS_KEY0`                   | `C.024`           | Access key level `0` changed.                                                           |
| `0x21` | `CHANGE_ACCESS_KEY1`                   | `C.025`           | Access key level `1` changed.                                                           |
| `0x22` | `CHANGE_ACCESS_KEY2`                   | `C.026`           | Access key level `2` changed.                                                           |
| `0x23` | `CHANGE_ACCESS_KEY3`                   | `C.027`           | Access key level `3` changed.                                                           |
| `0x24` | `CHANGE_PARAMETERS_LOCAL`              | `C.028`           | Parameters changed locally.                                                             |
| `0x25` | `CHANGE_PARAMETERS_REMOTE`             | `C.029`           | Parameters changed remotely.                                                            |
| `0x26` | `CMD_SET_DATETIME`                     | `C.030`           | Time set command received. Time set.                                                    |
| `0x27` | `CMD_RELAY_ON`                         | `C.031`           | `Relay on` command received.                                                            |
| `0x28` | `CMD_RELAY_OFF`                        | `C.032`           | `Relay off` command received.                                                           |
| `0x31` | `ENERGY_REGISTER_OVERFLOW`             | `C.049`           | Energy accumulation register overflow.                                                  |
| `0x32` | `CHANGE_TARIFF_TABLE`                  | `C.050`           | Tariff plan changed.                                                                    |
| `0x33` | `SET_TARIFF_TABLE`                     | `C.051`           | New tariff plan received.                                                               |
| `0x34` | `SUMMER_TIME`                          | `C.052`           | Switched to summer time.                                                                |
| `0x35` | `WINTER_TIME`                          | `C.053`           | Switched to winter time.                                                                |
| `0x36` | `RELAY_ON`                             | `C.054`           | Relay turned on.                                                                        |
| `0x37` | `RELAY_OFF`                            | `C.055`           | Relay turned off.                                                                       |
| `0x38` | `RESTART`                              | `C.056`           | Microcontroller program restart.                                                        |
| `0x39` | `WATCHDOG_RESTART`                     | `C.057`           | Watchdog restart.                                                                       |
| `0x40` | `VA_MAX_OK`                            | `C.064`           | Voltage phase `A` returned to normal after high.                                        |
| `0x41` | `VA_MAX_OVER`                          | `C.065`           | Voltage phase `A` above maximum threshold.                                              |
| `0x42` | `VA_MIN_OK`                            | `C.066`           | Voltage phase `A` returned to normal after low.                                         |
| `0x43` | `VA_MIN_UNDER`                         | `C.067`           | Voltage phase `A` below minimum threshold.                                              |
| `0x44` | `VB_MAX_OK`                            | `C.068`           | Voltage phase `B` returned to normal after high.                                        |
| `0x45` | `VB_MAX_OVER`                          | `C.069`           | Voltage phase `B` above maximum threshold.                                              |
| `0x46` | `VB_MIN_OK`                            | `C.070`           | Voltage phase `B` returned to normal after low.                                         |
| `0x47` | `VB_MIN_UNDER`                         | `C.071`           | Voltage phase `B` below minimum threshold.                                              |
| `0x48` | `VC_MAX_OK`                            | `C.072`           | Voltage phase `C` returned to normal after high.                                        |
| `0x49` | `VC_MAX_OVER`                          | `C.073`           | Voltage phase `C` above maximum threshold.                                              |
| `0x4A` | `VC_MIN_OK`                            | `C.074`           | Voltage phase `C` returned to normal after low.                                         |
| `0x4B` | `VC_MIN_UNDER`                         | `C.075`           | Voltage phase `C` below minimum threshold.                                              |
| `0x4C` | `F_MAX_OK`                             | `C.076`           | Frequency returned to normal after high.                                                |
| `0x4D` | `F_MAX_OVER`                           | `C.077`           | Frequency above maximum threshold.                                                      |
| `0x4E` | `F_MIN_OK`                             | `C.078`           | Frequency returned to normal after low.                                                 |
| `0x4F` | `F_MIN_UNDER`                          | `C.079`           | Frequency below minimum threshold.                                                      |
| `0x50` | `T_MAX_OK`                             | `C.080`           | Temperature returned to normal after high.                                              |
| `0x51` | `T_MAX_OVER`                           | `C.081`           | Temperature above maximum threshold.                                                    |
| `0x52` | `T_MIN_OK`                             | `C.082`           | Temperature returned to normal after low.                                               |
| `0x53` | `T_MIN_UNDER`                          | `C.083`           | Temperature below minimum threshold.                                                    |
| `0x54` | `IA_MAX_OK`                            | `C.084`           | Current phase `A` returned to normal after high.                                        |
| `0x55` | `IA_MAX_OVER`                          | `C.085`           | Current phase `A` above maximum threshold.                                              |
| `0x56` | `IB_MAX_OK`                            | `C.086`           | Current phase `B` returned to normal after high.                                        |
| `0x57` | `IB_MAX_OVER`                          | `C.087`           | Current phase `B` above maximum threshold.                                              |
| `0x58` | `IC_MAX_OK`                            | `C.088`           | Current phase `C` returned to normal after high.                                        |
| `0x59` | `IC_MAX_OVER`                          | `C.089`           | Current phase `C` above maximum threshold.                                              |
| `0x5A` | `PA_MAX_OK`                            | `C.090`           | Active power returned to normal after high.                                             |
| `0x5B` | `PA_MAX_OVER`                          | `C.091`           | Active power above maximum threshold.                                                   |
| `0x5C` | `PV_MAX_OK`                            | `C.092`           | Reactive power returned to normal after high.                                           |
| `0x5D` | `PV_MAX_OVER`                          | `C.093`           | Reactive power above maximum threshold.                                                 |
| `0x5E` | `IDIFF_OK`                             | `C.094`           | Differential current returned to normal after high.                                     |
| `0x5F` | `IDIFF_OVER`                           | `C.095`           | Differential current above maximum threshold.                                           |
| `0x60` | `CLOCK_OK`                             | `C.096`           | Real-time clock returned to normal.                                                     |
| `0x61` | `CLOCK_FAULT`                          | `C.097`           | Real-time clock fault.                                                                  |
| `0x62` | `POWER_C_ON`                           | `C.098`           | Phase `C` voltage turned on.                                                            |
| `0x63` | `POWER_C_OFF`                          | `C.099`           | Phase `C` voltage turned off.                                                           |
| `0x64` | `POWER_B_ON`                           | `C.100`           | Phase `B` voltage turned on.                                                            |
| `0x65` | `POWER_B_OFF`                          | `C.101`           | Phase `B` voltage turned off.                                                           |
| `0x66` | `POWER_A_ON`                           | `C.102`           | Phase `A` voltage turned on.                                                            |
| `0x67` | `POWER_A_OFF`                          | `C.103`           | Phase `A` voltage turned off.                                                           |
| `0x68` | `BATTERY_OK`                           | `C.104`           | Normal battery voltage restored.                                                        |
| `0x69` | `BATTERY_FAULT`                        | `C.105`           | Low battery voltage.                                                                    |
| `0x6A` | `CALIBRATION_OK`                       | `C.106`           | Calibration parameters set.                                                             |
| `0x6B` | `CALIBRATION_FAULT`                    | `C.107`           | Calibration parameters lost.                                                            |
| `0x6C` | `V_PARAMETERS_OK`                      | `C.108`           | Factory parameters set.                                                                 |
| `0x6D` | `V_PARAMETERS_FAULT`                   | `C.109`           | Factory parameters lost.                                                                |
| `0x6E` | `O_PARAMETERS_OK`                      | `C.110`           | Parameters set.                                                                         |
| `0x6F` | `O_PARAMETERS_FAULT`                   | `C.111`           | Parameters lost.                                                                        |
| `0x70` | `CHANGE_COR_TIME`                      | `C.112`           | Daylight saving time transition parameters changed.                                     |
| `0x71` | `CMD_RELAY_2_ON`                       | `C.113`           | Second relay turned on.                                                                 |
| `0x72` | `CMD_RELAY_2_OFF`                      | `C.114`           | Second relay turned off.                                                                |
| `0x73` | `CROSS_ZERO_EN_T1`                     | `C.115`           | Active energy counter tariff `1` crossed zero at `1000000.00` `kW`.                     |
| `0x74` | `CROSS_ZERO_EN_T2`                     | `C.116`           | Active energy counter tariff `2` crossed zero at `1000000.00` `kW`.                     |
| `0x75` | `CROSS_ZERO_EN_T3`                     | `C.117`           | Active energy counter tariff `3` crossed zero at `1000000.00` `kW`.                     |
| `0x76` | `CROSS_ZERO_EN_T4`                     | `C.118`           | Active energy counter tariff `4` crossed zero at `1000000.00` `kW`.                     |
| `0x77` | `CROSS_ZERO_VARI_T1`                   | `C.119`           | Reactive positive energy counter tariff `1` crossed zero at `1000000.00` `kVar`.        |
| `0x78` | `CROSS_ZERO_VARI_T2`                   | `C.120`           | Reactive positive energy counter tariff `2` crossed zero at `1000000.00` `kVar`.        |
| `0x79` | `CROSS_ZERO_VARI_T3`                   | `C.121`           | Reactive positive energy counter tariff `3` crossed zero at `1000000.00` `kVar`.        |
| `0x7A` | `CROSS_ZERO_VARI_T4`                   | `C.122`           | Reactive positive energy counter tariff `4` crossed zero at `1000000.00` `kVar`.        |
| `0x7B` | `CROSS_ZERO_VARE_T1`                   | `C.123`           | Reactive negative energy counter tariff `1` crossed zero at `1000000.00` `kVar`.        |
| `0x7C` | `CROSS_ZERO_VARE_T2`                   | `C.124`           | Reactive negative energy counter tariff `2` crossed zero at `1000000.00` `kVar`.        |
| `0x7D` | `CROSS_ZERO_VARE_T3`                   | `C.125`           | Reactive negative energy counter tariff `3` crossed zero at `1000000.00` `kVar`.        |
| `0x7E` | `CROSS_ZERO_VARE_T4`                   | `C.126`           | Reactive negative energy counter tariff `4` crossed zero at `1000000.00` `kVar`.        |
| `0x7F` | `CALIBRATION_FLAG_SET`                 | `C.127`           | Calibration flag set.                                                                   |
| `0x80` | `CALIBRATION_FLAG_RESET`               | `C.128`           | Calibration flag reset.                                                                 |
| `0x81` | `BAD_TEST_EEPROM`                      | `C.129`           | EEPROM test failed.                                                                     |
| `0x82` | `BAD_TEST_FRAM`                        | `C.130`           | FRAM test failed.                                                                       |
| `0x83` | `SET_NEW_SALDO`                        | `C.131`           | New prepayment received.                                                                |
| `0x84` | `SALDO_PARAMETERS_FAULT`               | `C.132`           | Saldo parameters lost.                                                                  |
| `0x85` | `ACCUMULATION_PARAMETERS_FAULT`        | `C.133`           | Accumulation parameters lost.                                                           |
| `0x86` | `ACCUMULATION_PARAMETERS_EXT_FAULT`    | `C.134`           | Additional accumulation parameters lost.                                                |
| `0x87` | `CALCULATION_PERIOD_FAULT`             | `C.135`           | Calculation period data lost.                                                           |
| `0x88` | `BLOCK_TARIFF_FAULT`                   | `C.136`           | Block tariff parameters lost.                                                           |
| `0x89` | `CALIBRATION_PARAMETERS_FAULT`         | `C.137`           | Calibration parameters lost.                                                            |
| `0x8A` | `WINTER_SUMMER_FAULT`                  | `C.138`           | Winter/summer transition parameters lost.                                               |
| `0x8B` | `OPERATOR_PARAMETERS_VALUES_FAULT`     | `C.139`           | Operator parameters lost.                                                               |
| `0x8C` | `OPERATOR_PARAMETERS_EXT_VALUES_FAULT` | `C.140`           | Additional operator parameters lost.                                                    |
| `0x8D` | `SALDO_ENERGY_FAULT`                   | `C.141`           | Saldo energy values lost.                                                               |
| `0x8E` | `TIME_CORRECT`                         | `C.142`           | Time correction.                                                                        |
| `0x8F` | `COEFFICIENT_TRANSFORMATION_CHANGE`    | `C.143`           | Transformation coefficients changed.                                                    |
| `0x90` | `RELAY_HARD_BAD_OFF`                   | `C.144`           | Relay mechanically turned off.                                                          |
| `0x91` | `RELAY_HARD_ON`                        | `C.145`           | Relay turned on after mechanical impact. Relay state restored.                          |
| `0x93` | `RELAY_HARD_BAD_ON`                    | `C.146`           | Relay mechanically turned on.                                                           |
| `0x94` | `RELAY_HARD_OFF`                       | `C.147`           | Relay turned off after mechanical impact. Relay state restored.                         |
| `0x95` | `METER_TROUBLE`                        | `C.148`           | Meter malfunction.                                                                      |
| `0x96` | `CASE_TERMINAL_BOX_OPENED`             | `C.149`           | Terminal box opened.                                                                    |
| `0x97` | `CASE_TERMINAL_BOX_CLOSED`             | `C.150`           | Terminal box closed.                                                                    |
| `0x98` | `CHANGE_TARIFF_TABLE_2`                | `C.151`           | Tariff plan `2` changed.                                                                |
| `0x99` | `CHANGE_TARIFF_TABLE_3`                | `C.152`           | Tariff plan `3` changed.                                                                |
| `0x9A` | `CASE_MODULE_OPENED`                   | `C.153`           | Meter module compartment opened.                                                        |
| `0x9B` | `CASE_MODULE_CLOSED`                   | `C.154`           | Meter module compartment closed.                                                        |
| `0x9C` | `SET_SALDO_PARAM`                      | `C.155`           | Saldo parameters set.                                                                   |
| `0x9D` | `POWER_OVER_RELAY_OFF`                 | `C.156`           | Relay turned off after exceeding active power (since firmware version >= `302.15.001`). |
| `0x9E` | `CHANGE_PARAMETER_CHANNEL1`            | `C.157`           | Load profile parameter `1` changed (since firmware version >= `302.17.001`).            |
| `0x9F` | `CHANGE_PARAMETER_CHANNEL2`            | `C.158`           | Load profile parameter `2` changed.                                                     |
| `0xA0` | `CHANGE_PARAMETER_CHANNEL3`            | `C.159`           | Load profile parameter `3` changed.                                                     |
| `0xA1` | `CHANGE_PARAMETER_CHANNEL4`            | `C.160`           | Load profile parameter `4` changed.                                                     |
| `0xA2` | `CHANGE_PARAMETER_CHANNEL5`            | `C.161`           | Load profile parameter `5` changed.                                                     |
| `0xA3` | `CHANGE_PARAMETER_CHANNEL6`            | `C.162`           | Load profile parameter `6` changed.                                                     |
| `0xA4` | `CROSS_ZERO_EXPORT_EN_T1`              | `C.163`           | Active export energy counter tariff `1` crossed zero at `1000000.00` `kW`.              |
| `0xA5` | `CROSS_ZERO_EXPORT_EN_T2`              | `C.164`           | Active export energy counter tariff `2` crossed zero at `1000000.00` `kW`.              |
| `0xA6` | `CROSS_ZERO_EXPORT_EN_T3`              | `C.165`           | Active export energy counter tariff `3` crossed zero at `1000000.00` `kW`.              |
| `0xA7` | `CROSS_ZERO_EXPORT_EN_T4`              | `C.166`           | Active export energy counter tariff `4` crossed zero at `1000000.00` `kW`.              |
| `0xA8` | `CROSS_ZERO_EXPORT_VARI1`              | `C.167`           | Reactive positive energy counter (`Q3`) tariff `1` crossed zero at `1000000.00` `kVar`. |
| `0xA9` | `CROSS_ZERO_EXPORT_VARI2`              | `C.168`           | Reactive positive energy counter (`Q3`) tariff `2` crossed zero at `1000000.00` `kVar`. |
| `0xAA` | `CROSS_ZERO_EXPORT_VARI3`              | `C.169`           | Reactive positive energy counter (`Q3`) tariff `3` crossed zero at `1000000.00` `kVar`. |
| `0xAB` | `CROSS_ZERO_EXPORT_VARI4`              | `C.170`           | Reactive positive energy counter (`Q3`) tariff `4` crossed zero at `1000000.00` `kVar`. |
| `0xAC` | `CROSS_ZERO_EXPORT_VARE1`              | `C.171`           | Reactive negative energy counter (`Q2`) tariff `1` crossed zero at `1000000.00` `kVar`. |
| `0xAD` | `CROSS_ZERO_EXPORT_VARE2`              | `C.172`           | Reactive negative energy counter (`Q2`) tariff `2` crossed zero at `1000000.00` `kVar`. |
| `0xAE` | `CROSS_ZERO_EXPORT_VARE3`              | `C.173`           | Reactive negative energy counter (`Q2`) tariff `3` crossed zero at `1000000.00` `kVar`. |
| `0xAF` | `CROSS_ZERO_EXPORT_VARE4`              | `C.174`           | Reactive negative energy counter (`Q2`) tariff `4` crossed zero at `1000000.00` `kVar`. |
| `0xB0` | `EM_MAGNETIC_INFLUENCE_ON`             | `C.175`           | Presence of alternating magnetic field detected.                                        |
| `0xB1` | `EM_MAGNETIC_INFLUENCE_OFF`            | `C.176`           | Alternating magnetic field influence ended.                                             |
| `0xB2` | `RESET_EM_FLAG`                        | `C.177`           | Electromagnetic impact screen reset.                                                    |
| `0xB3` | `RESET_MAGNETIC_FLAG`                  | `C.178`           | Magnetic impact screen reset.                                                           |
| `0xE0` | `SET_DEMAND_EN_1_MIN`                  | `C.224`           | `1`-minute energy, voltage load profiles recording mode set.                            |
| `0xE1` | `SET_DEMAND_EN_3_MIN`                  | `C.225`           | `3`-minute energy, voltage load profiles recording mode set.                            |
| `0xE2` | `SET_DEMAND_EN_5_MIN`                  | `C.226`           | `5`-minute energy, voltage load profiles recording mode set.                            |
| `0xE3` | `SET_DEMAND_EN_10_MIN`                 | `C.227`           | `10`-minute energy, voltage load profiles recording mode set.                           |
| `0xE4` | `SET_DEMAND_EN_15_MIN`                 | `C.228`           | `15`-minute energy, voltage load profiles recording mode set.                           |
| `0xE5` | `SET_DEMAND_EN_30_MIN`                 | `C.229`           | `30`-minute energy, voltage load profiles recording mode set.                           |
| `0xE6` | `SET_DEMAND_EN_60_MIN`                 | `C.230`           | `60`-minute energy, voltage load profiles recording mode set.                           |
| `0xE7` | `P_MAX_A_MINUS_OK`                     | `C.231`           | Recovery of permissible generated power `P-` after being too high.                      |
| `0xE8` | `P_MAX_A_MINUS_OVER`                   | `C.232`           | Generated power `P-` exceeds the maximum power threshold.                               |
