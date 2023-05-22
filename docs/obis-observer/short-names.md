# Short names with OBIS codes

Short name is a one-byte number that will be used in all messages to represent the OBIS code.

`1`-`199` - [static names](#static) that can't be changed.
`210`-`235` - [reassignable names](#reassignable).


## Static

### General

| Short name | OBIS code | Description                                                             |
| ---------- | --------- | ----------------------------------------------------------------------- |
| `1`        | `1.4.0`   | active power+ (`QI`+`QIV`), current avg. `1`                            |
| `2`        | `1.5.0`   | active power+ (`QI`+`QIV`), average                                     |
| `3`        | `1.6.0`   | active power+ (`QI`+`QIV`), maximum, total                              |
| `4`        | `1.6.1`   | active power+ (`QI`+`QIV`), maximum, tariff `T1`                        |
| `5`        | `1.6.2`   | active power+ (`QI`+`QIV`), maximum, tariff `T2`                        |
| `6`        | `1.6.3`   | active power+ (`QI`+`QIV`), maximum, tariff `T3`                        |
| `7`        | `1.6.4`   | active power+ (`QI`+`QIV`), maximum, tariff `T4`                        |
| `8`        | `1.8.0`   | active power+ (`QI`+`QIV`), total                                       |
| `9`        | `1.8.1`   | active power+ (`QI`+`QIV`), tariff `T1`                                 |
| `10`       | `1.8.2`   | active power+ (`QI`+`QIV`), tariff `T2`                                 |
| `11`       | `1.8.3`   | active power+ (`QI`+`QIV`), tariff `T3`                                 |
| `12`       | `1.8.4`   | active power+ (`QI`+`QIV`), tariff `T4`                                 |
| `13`       | `2.4.0`   | active power- (`QII`+`QIII`), current avg. `1`                          |
| `14`       | `2.5.0`   | active power- (`QII`+`QIII`), average                                   |
| `15`       | `2.6.0`   | active power- (`QII`+`QIII`), maximum, total                            |
| `16`       | `2.6.1`   | active power- (`QII`+`QIII`), maximum, tariff `T1`                      |
| `17`       | `2.6.2`   | active power- (`QII`+`QIII`), maximum, tariff `T2`                      |
| `18`       | `2.6.3`   | active power- (`QII`+`QIII`), maximum, tariff `T3`                      |
| `19`       | `2.6.4`   | active power- (`QII`+`QIII`), maximum, tariff `T4`                      |
| `20`       | `2.8.0`   | active power- (`QII`+`QIII`), total                                     |
| `21`       | `2.8.1`   | active power- (`QII`+`QIII`), tariff `T1`                               |
| `22`       | `2.8.2`   | active power- (`QII`+`QIII`), tariff `T2`                               |
| `23`       | `2.8.3`   | active power- (`QII`+`QIII`), tariff `T3`                               |
| `24`       | `2.8.4`   | active power- (`QII`+`QIII`), tariff `T4`                               |
| `25`       | `3.4.0`   | reactive power+ (`QI`+`QII`), current avg. `1`                          |
| `26`       | `3.5.0`   | reactive power+ (`QI`+`QII`), average                                   |
| `27`       | `3.6.0`   | reactive power+ (`QI`+`QII`), maximum, total                            |
| `28`       | `3.6.1`   | reactive power+ (`QI`+`QII`), maximum, tariff `T1`                      |
| `39`       | `3.6.2`   | reactive power+ (`QI`+`QII`), maximum, tariff `T2`                      |
| `30`       | `3.6.3`   | reactive power+ (`QI`+`QII`), maximum, tariff `T3`                      |
| `31`       | `3.6.4`   | reactive power+ (`QI`+`QII`), maximum, tariff `T4`                      |
| `32`       | `3.8.0`   | reactive power+ (`QI`+`QII`), total                                     |
| `33`       | `3.8.1`   | reactive power+ (`QI`+`QII`), tariff `T1`                               |
| `34`       | `3.8.2`   | reactive power+ (`QI`+`QII`), tariff `T2`                               |
| `35`       | `3.8.3`   | reactive power+ (`QI`+`QII`), tariff `T3`                               |
| `36`       | `3.8.4`   | reactive power+ (`QI`+`QII`), tariff `T4`                               |
| `37`       | `4.4.0`   | reactive power– (`QIII`+`QIV`), current avg. `1`                        |
| `38`       | `4.5.0`   | reactive power– (`QIII`+`QIV`), average                                 |
| `39`       | `4.6.0`   | reactive power– (`QIII`+`QIV`), maximum, total                          |
| `40`       | `4.6.1`   | reactive power– (`QIII`+`QIV`), maximum, tariff `T1`                    |
| `41`       | `4.6.2`   | reactive power– (`QIII`+`QIV`), maximum, tariff `T2`                    |
| `42`       | `4.6.3`   | reactive power– (`QIII`+`QIV`), maximum, tariff `T3`                    |
| `43`       | `4.6.4`   | reactive power– (`QIII`+`QIV`), maximum, tariff `T4`                    |
| `44`       | `4.8.0`   | reactive power– (`QIII`+`QIV`), total                                   |
| `45`       | `4.8.1`   | reactive power– (`QIII`+`QIV`), tariff `T1`                             |
| `46`       | `4.8.2`   | reactive power– (`QIII`+`QIV`), tariff `T2`                             |
| `47`       | `4.8.3`   | reactive power– (`QIII`+`QIV`), tariff `T3`                             |
| `48`       | `4.8.4`   | reactive power– (`QIII`+`QIV`), tariff `T4`                             |
| `49`       | `5.4.0`   | reactive power `QI`, current avg. `1`                                   |
| `50`       | `5.5.0`   | reactive power `QI`, average                                            |
| `51`       | `5.6.0`   | reactive power `QI`, maximum, total                                     |
| `52`       | `5.6.1`   | reactive power `QI`, maximum, tariff `T1`                               |
| `53`       | `5.6.2`   | reactive power `QI`, maximum, tariff `T2`                               |
| `54`       | `5.6.3`   | reactive power `QI`, maximum, tariff `T3`                               |
| `55`       | `5.6.4`   | reactive power `QI`, maximum, tariff `T4`                               |
| `56`       | `5.8.0`   | reactive power `QI`, total                                              |
| `57`       | `5.8.1`   | reactive power `QI`, tariff `T1`                                        |
| `58`       | `5.8.2`   | reactive power `QI`, tariff `T2`                                        |
| `59`       | `5.8.3`   | reactive power `QI`, tariff `T3`                                        |
| `60`       | `5.8.4`   | reactive power `QI`, tariff `T4`                                        |
| `61`       | `6.4.0`   | reactive power `QII`, current avg. `1`                                  |
| `62`       | `6.5.0`   | reactive power `QII`, average                                           |
| `63`       | `6.6.0`   | reactive power `QII`, maximum, total                                    |
| `64`       | `6.6.1`   | reactive power `QII`, maximum, tariff `T1`                              |
| `65`       | `6.6.2`   | reactive power `QII`, maximum, tariff `T2`                              |
| `66`       | `6.6.3`   | reactive power `QII`, maximum, tariff `T3`                              |
| `67`       | `6.6.4`   | reactive power `QII`, maximum, tariff `T4`                              |
| `68`       | `6.8.0`   | reactive power `QII`, total                                             |
| `69`       | `6.8.1`   | reactive power `QII`, tariff `T1`                                       |
| `70`       | `6.8.2`   | reactive power `QII`, tariff `T2`                                       |
| `71`       | `6.8.3`   | reactive power `QII`, tariff `T3`                                       |
| `72`       | `6.8.4`   | reactive power `QII`, tariff `T4`                                       |
| `73`       | `7.4.0`   | reactive power `QIII`, current avg. `1`                                 |
| `74`       | `7.5.0`   | reactive power `QIII`, average                                          |
| `75`       | `7.6.0`   | reactive power `QIII`, maximum, total                                   |
| `76`       | `7.6.1`   | reactive power `QIII`, maximum, tariff `T1`                             |
| `77`       | `7.6.2`   | reactive power `QIII`, maximum, tariff `T2`                             |
| `78`       | `7.6.3`   | reactive power `QIII`, maximum, tariff `T3`                             |
| `79`       | `7.6.4`   | reactive power `QIII`, maximum, tariff `T4`                             |
| `80`       | `7.8.0`   | reactive power `QIII`, total                                            |
| `81`       | `7.8.1`   | reactive power `QIII`, tariff `T1`                                      |
| `82`       | `7.8.2`   | reactive power `QIII`, tariff `T2`                                      |
| `83`       | `7.8.3`   | reactive power `QIII`, tariff `T3`                                      |
| `84`       | `7.8.4`   | reactive power `QIII`, tariff `T4`                                      |
| `85`       | `8.4.0`   | reactive power `QIV`, current avg. `1`                                  |
| `86`       | `8.5.0`   | reactive power `QIV`, average                                           |
| `87`       | `8.6.0`   | reactive power `QIV`, maximum, total                                    |
| `88`       | `8.6.1`   | reactive power `QIV`, maximum, tariff `T1`                              |
| `89`       | `8.6.2`   | reactive power `QIV`, maximum, tariff `T2`                              |
| `90`       | `8.6.3`   | reactive power `QIV`, maximum, tariff `T3`                              |
| `91`       | `8.6.4`   | reactive power `QIV`, maximum, tariff `T4`                              |
| `92`       | `8.8.0`   | reactive power `QIV`, total                                             |
| `93`       | `8.8.1`   | reactive power `QIV`, tariff `T1`                                       |
| `94`       | `8.8.2`   | reactive power `QIV`, tariff `T2`                                       |
| `95`       | `8.8.3`   | reactive power `QIV`, tariff `T3`                                       |
| `96`       | `8.8.4`   | reactive power `QIV`, tariff `T4`                                       |
| `97`       | `9.5.0`   | apparent power+ (`QI`+`QIV`), average                                   |
| `98`       | `9.8.0`   | apparent power+ (`QI`+`QIV`), total                                     |
| `99`       | `10.5.0`  | apparent power– (`QII`+`QIII`), average                                 |
| `100`      | `10.8.0`  | apparent power– (`QII`+`QIII`), total                                   |
| `101`      | `15.4.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), current avg. `1`     |
| `102`      | `15.5.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), average              |
| `103`      | `15.6.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), maximum, total       |
| `104`      | `15.6.1`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), maximum, tariff `T1` |
| `105`      | `15.6.2`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), maximum, tariff `T2` |
| `106`      | `15.6.3`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), maximum, tariff `T3` |
| `107`      | `15.6.4`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), maximum, tariff `T4` |
| `108`      | `15.8.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), total                |
| `109`      | `15.8.1`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), tariff `T1`          |
| `110`      | `15.8.2`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), tariff `T2`          |
| `111`      | `15.8.3`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), tariff `T3`          |
| `112`      | `15.8.4`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), tariff `T4`          |
| `113`      | `16.4.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), current avg. `1`      |
| `114`      | `16.5.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), average               |
| `115`      | `16.6.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), maximum, total        |
| `116`      | `16.6.1`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), maximum, tariff `T1`  |
| `117`      | `16.6.2`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), maximum, tariff `T2`  |
| `118`      | `16.6.3`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), maximum, tariff `T3`  |
| `119`      | `16.6.4`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), maximum, tariff `T4`  |
| `120`      | `16.8.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), total                 |
| `121`      | `16.8.1`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), tariff `T1`           |
| `122`      | `16.8.2`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), tariff `T2`           |
| `123`      | `16.8.3`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), tariff `T3`           |
| `124`      | `16.8.4`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), tariff `T4`           |
| `125`      | `11.5.0`  | current phase `L1` average                                              |
| `126`      | `31.5.0`  | current phase `L1` average                                              |
| `127`      | `51.5.0`  | current phase `L2` average                                              |
| `128`      | `71.5.0`  | current phase `L3` average                                              |
| `129`      | `91.5.0`  | current neutral average                                                 |
| `130`      | `12.5.0`  | voltage average                                                         |
| `131`      | `32.5.0`  | voltage phase `L1` average                                              |
| `132`      | `52.5.0`  | voltage phase `L2` average                                              |
| `133`      | `72.5.0`  | voltage phase `L3` average                                              |

### Instantaneous

| Short name | OBIS code | Description                                             |
| ---------- | --------- | ------------------------------------------------------- |
| `134`      | `1.7.0`   | active power+ (`QI`+`QIV`)                              |
| `135`      | `21.7.0`  | active power+ (`QI`+`QIV`), `L1`                        |
| `136`      | `41.7.0`  | active power+ (`QI`+`QIV`), `L2`                        |
| `137`      | `61.7.0`  | active power+ (`QI`+`QIV`), `L3`                        |
| `138`      | `2.7.0`   | active power- (`QII`+`QIII`)                            |
| `139`      | `22.7.0`  | active power- (`QII`+`QIII`), `L1`                      |
| `140`      | `42.7.0`  | active power- (`QII`+`QIII`), `L2`                      |
| `141`      | `62.7.0`  | active power- (`QII`+`QIII`), `L3`                      |
| `142`      | `3.7.0`   | reactive power+ (`QI`+`QII`)                            |
| `143`      | `23.7.0`  | reactive power+ (`QI`+`QII`), `L1`                      |
| `144`      | `43.7.0`  | reactive power+ (`QI`+`QII`), `L2`                      |
| `145`      | `63.7.0`  | reactive power+ (`QI`+`QII`), `L3`                      |
| `146`      | `4.7.0`   | reactive power- (`QIII`+`QIV`)                          |
| `147`      | `24.7.0`  | reactive power- (`QIII`+`QIV`), `L1`                    |
| `148`      | `44.7.0`  | reactive power- (`QIII`+`QIV`), `L2`                    |
| `149`      | `64.7.0`  | reactive power- (`QIII`+`QIV`), `L3`                    |
| `150`      | `11.7.0`  | current                                                 |
| `151`      | `31.7.0`  | current, `L1`                                           |
| `152`      | `51.7.0`  | current, `L2`                                           |
| `153`      | `71.7.0`  | current, `L3`                                           |
| `154`      | `12.7.0`  | voltage                                                 |
| `155`      | `32.7.0`  | voltage, `L1`                                           |
| `156`      | `52.7.0`  | voltage, `L2`                                           |
| `157`      | `72.7.0`  | voltage, `L3`                                           |
| `158`      | `13.7.0`  | sum Li Power factor                                     |
| `159`      | `33.7.0`  | power factor, `L1`                                      |
| `160`      | `53.7.0`  | power factor, `L2`                                      |
| `161`      | `73.7.0`  | power factor, `L3`                                      |
| `162`      | `14.7.0`  | sum supply frequency                                    |
| `163`      | `34.7.0`  | supply frequency, `L1`                                  |
| `164`      | `54.7.0`  | supply frequency, `L2`                                  |
| `165`      | `74.7.0`  | supply frequency, `L3`                                  |
| `166`      | `15.7.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`))       |
| `167`      | `35.7.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), `L1` |
| `168`      | `55.7.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), `L2` |
| `169`      | `75.7.0`  | active power (abs(`QI`+`QIV`)+(abs(`QII`+`QIII`)), `L3` |
| `170`      | `16.7.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`))        |
| `171`      | `36.7.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), `L1`  |
| `172`      | `56.7.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), `L2`  |
| `173`      | `76.7.0`  | active power (abs(`QI`+`QIV`)-abs(`QII`+`QIII`)), `L3`  |
| `174`      | `17.7.0`  | active power `QI`                                       |
| `175`      | `37.7.0`  | active power `QI`, `L1`                                 |
| `176`      | `57.7.0`  | active power `QI`, `L2`                                 |
| `177`      | `77.7.0`  | active power `QI`, `L3`                                 |
| `178`      | `18.7.0`  | active power `QII`                                      |
| `179`      | `38.7.0`  | active power `QII`, `L1`                                |
| `180`      | `58.7.0`  | active power `QII`, `L2`                                |
| `181`      | `78.7.0`  | active power `QII`, `L3`                                |
| `182`      | `19.7.0`  | active power `QIII`                                     |
| `183`      | `39.7.0`  | active power `QIII`, `L1`                               |
| `184`      | `59.7.0`  | active power `QIII`, `L2`                               |
| `185`      | `79.7.0`  | active power `QIII`, `L3`                               |
| `186`      | `20.7.0`  | active power `QIV`                                      |
| `187`      | `40.7.0`  | active power `QIV`, `L1`                                |
| `188`      | `60.7.0`  | active power `QIV`, `L2`                                |
| `189`      | `80.7.0`  | active power `QIV`, `L3`                                |
| `190`      | `81.7.1`  | angle of U(`L2`) - U(`L1`)                              |
| `191`      | `81.7.2`  | angle of U(`L3`) - U(`L2`)                              |
| `192`      | `91.7.0`  | `L0` current (neutral)                                  |

### Abstract

| Short name | OBIS code   | Description                |
| ---------- | ----------- | -------------------------- |
| `193`      | `0.0.0`     | device ID                  |
| `194`      | `0.2.0`     | active firmware identifier |
| `195`      | `0.2.1`     | active firmware version    |
| `196`      | `0.2.8`     | active firmware signature  |
| `197`      | `0.9.1`     | local time                 |
| `198`      | `0.9.2`     | local date                 |
| `199`      | `F.F.0*255` | fatal error meter status   |


## Reassignable

| Short name | OBIS code | Description                                                                        |
| ---------- | --------- | ---------------------------------------------------------------------------------- |
| `210`      | `C.5.0`   | internal operating status, global                                                  |
| `211`      | `C.5.1`   | internal operating status (status word `1`)                                        |
| `212`      | `C.5.2`   | internal operating status (status word `2`)                                        |
| `213`      | `C.5.3`   | internal operating status (status word `3`)                                        |
| `214`      | `C.5.4`   | internal operating status (status word `4`)                                        |
| `215`      | `C.5.5`   | meter started status flag                                                          |
| `216`      | `C.7.0`   | number of power failures                                                           |
| `217`      | `C.7.5`   | number of long power failures                                                      |
| `218`      | `C.10.0`  | status information missing voltage                                                 |
| `219`      | `C.10.1`  | status information missing current                                                 |
| `220`      | `C.10.2`  | status information current without voltage                                         |
| `221`      | `C.10.3`  | status information auxiliary power supply                                          |
| `222`      | `C.20.0`  | meter open event counter                                                           |
| `223`      | `C.20.1`  | meter open event, time stamp of current event occurrence                           |
| `224`      | `C.20.5`  | terminal cover open event counter                                                  |
| `225`      | `C.20.6`  | terminal cover open event, time stamp of current event occurrence                  |
| `226`      | `C.20.10` | tilt event counter                                                                 |
| `227`      | `C.20.11` | tilt event, time stamp of current event occurrence                                 |
| `228`      | `C.20.15` | strong DC magnetic field event counter                                             |
| `229`      | `C.20.16` | strong DC magnetic field event, time stamp of current event occurrence             |
| `230`      | `C.20.20` | supply control switch / valve tamper event counter                                 |
| `231`      | `C.20.21` | supply control switch / valve tamper event, time stamp of current event occurrence |
| `232`      | `C.20.25` | metrology tamper event counter                                                     |
| `233`      | `C.20.26` | metrology tamper event, time stamp of current event occurrence                     |
| `234`      | `C.20.30` | communication tamper event counter                                                 |
| `235`      | `C.20.31` | communication tamper event, time stamp of current event occurrence                 |
