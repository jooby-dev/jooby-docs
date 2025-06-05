# GetEnergyDay

Request/response to get daily energies (`A+, R+, R-`) by default or selected energy type for all tariffs (`T1`-`T4`) for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1 without energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                           |
| `1`  | `uint8` | command size = `3`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |

#### case #2 with energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                           |
| `1`  | `uint8` | command size = `4`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |
| `1`  | `uint8` | [energy type](#energy-type)                   |

### Parameters

#### energy type

##### meter type `R`

| Energy type (x=`1`..`4`)                       | Value |
| ---------------------------------------------- | ----- |
| `A+` (`1.8.x`), `R+` (`3.8.x`), `R-` (`4.8.1`) | `1`   |

##### meter type `G`

| Energy type (`x`=`1`..`4`)                         | Value |
| -------------------------------------------------- | ----- |
| `A+` (`1.8.x`), `A+R+` (`5.8.x`), `A+R-` (`8.8.x`) | `1`   |
| `A-` (`2.8.x`), `A-R+` (`6.8.x`), `A-R-` (`7.8.x`) | `2`   |

### Examples

#### request the daily energies without energy type for 2024.03.22

| Field        | Value       | Hex    |
| ------------ | ----------- | ------ |
| command id   | `22`        | `0x16` |
| command size | `3`         | `0x03` |
| year         | `24`        | `0x18` |
| month        | `3` (March) | `0x03` |
| date         | `22`        | `0x16` |

Command hex dump: `16 03 18 03 16`

#### request the daily energies (`A+, R+, R-`) with energy type for 2024.03.22

| Field                       | Value                                          | Hex    |
| --------------------------- | ---------------------------------------------- | ------ |
| command id                  | `22`                                           | `0x16` |
| command size                | `4`                                            | `0x04` |
| year                        | `24`                                           | `0x18` |
| month                       | `3` (March)                                    | `0x03` |
| date                        | `22`                                           | `0x16` |
| [energy type](#energy-type) | `A+` (`1.8.x`), `R+` (`3.8.x`), `R-` (`4.8.1`) | `0x01` |

Command hex dump: `16 04 18 03 16 01`


## Response

### Format

#### response to request without energy type

| Size | Type    | Field                                                 |
| ---- | ------- | ----------------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                                   |
| `1`  | `uint8` | command size = `51`                                   |
| `1`  | `uint8` | year (number of years after `2000`)                   |
| `1`  | `uint8` | month (`1` - January ... `12` - December)             |
| `1`  | `uint8` | date (month day number which starts from `1`)         |
| `4`  | `int32` | active energy `A+` for tariff `T1` (`1.8.1`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` for tariff `T1` (`5.8.1`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` for tariff `T1` (`8.8.1`)       |
| `4`  | `int32` | active energy `A+` for tariff `T2` (`1.8.2`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` for tariff `T2` (`5.8.2`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` for tariff `T2` (`8.8.2`)       |
| `4`  | `int32` | active energy `A+` for tariff `T3` (`1.8.3`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` for tariff `T3` (`5.8.3`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` for tariff `T3` (`8.8.3`)       |
| `4`  | `int32` | active energy `A+` for tariff `T4` (`1.8.4`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` for tariff `T4` (`5.8.4`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` for tariff `T4` (`8.8.4`)       |

#### response to request with energy type

| Size  | Type    | Field                                                                                                                                                                                                    |
| ----- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id = `0x16`                                                                                                                                                                                      |
| `1`   | `uint8` | command size (dynamic, `4+`, max is `52`)                                                                                                                                                                |
| `1`   | `uint8` | year (number of years after `2000`)                                                                                                                                                                      |
| `1`   | `uint8` | month (`1` - January ... `12` - December)                                                                                                                                                                |
| `1`   | `uint8` | date (month day number which starts from `1`)                                                                                                                                                            |
| `1`   | `uint8` | packed energy type with tariff flags <br/>`BIT3`-`BIT0` - [energy type](#energy-type)<br/>`BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `4*n` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                      |

> `n` - the number of energies derived from packed energy type field.

### Examples

#### response to request without energy type

| Field            | Value       | Hex          |
| ---------------- | ----------- | ------------ |
| command id       | `22`        | `0x16`       |
| command size     | `51`        | `0x33`       |
| year             | `24`        | `0x18`       |
| month            | `3` (March) | `0x03`       |
| date             | `22`        | `0x16`       |
| `A+` (`1.8.1`)   | `40301230`  | `0x0266f2ae` |
| `A+R+` (`5.8.1`) | `3334244`   | `0x0032e064` |
| `A+R-` (`8.8.1`) | `2333`      | `0x0000091d` |
| `A+` (`1.8.2`)   | `2145623`   | `0x0020bd57` |
| `A+R+` (`5.8.2`) | `2145624`   | `0x0020bd58` |
| `A+R-` (`8.8.2`) | `2145625`   | `0x0020bd59` |
| `A+` (`1.8.3`)   | `2145626`   | `0x0020bd5a` |
| `A+R+` (`5.8.3`) | `2145627`   | `0x0020bd5b` |
| `A+R-` (`8.8.3`) | `2145628`   | `0x0020bd5c` |
| `A+` (`1.8.4`)   | `2145629`   | `0x0020bd5d` |
| `A+R+` (`5.8.4`) | `2145630`   | `0x0020bd5e` |
| `A+R-` (`8.8.4`) | `2145631`   | `0x0020bd5f` |

Command hex dump:
```
16 33
18 03 16
0266f2ae 0032e064 0000091d
0020bd57 0020bd58 0020bd59
0020bd5a 0020bd5b 0020bd5c
0020bd5d 0020bd5e 0020bd5f
```

#### response to request with energy type (`A+, R+, R-`)

| Field                       | Value                                                                                 | Hex          |
| --------------------------- | ------------------------------------------------------------------------------------- | ------------ |
| command id                  | `22`                                                                                  | `0x16`       |
| command size                | `16`                                                                                  | `0x10`       |
| year                        | `24`                                                                                  | `0x18`       |
| month                       | `3` (March)                                                                           | `0x03`       |
| date                        | `22`                                                                                  | `0x16`       |
| [energy type](#energy-type) | energy: `A-, R+, R-`<br>`T1`: `true`<br>`T2`: `false`<br>`T3`: `true`<br>`T4`: `true` | `0xd2`       |
| `A+` (`1.8.1`)              | `40301230`                                                                            | `0x0266f2ae` |
| `A+R+` (`5.8.1`)            | `3334244`                                                                             | `0x0032e064` |
| `A+R-` (`8.8.1`)            | `2333`                                                                                | `0x0000091d` |
| `A+` (`1.8.3`)              | `2145626`                                                                             | `0x0020bd5a` |
| `A+R+` (`5.8.3`)            | `2145627`                                                                             | `0x0020bd5b` |
| `A+R-` (`8.8.3`)            | `2145628`                                                                             | `0x0020bd5c` |
| `A+` (`1.8.4`)              | `2145629`                                                                             | `0x0020bd5d` |
| `A+R+` (`5.8.4`)            | `2145630`                                                                             | `0x0020bd5e` |
| `A+R-` (`8.8.4`)            | `2145631`                                                                             | `0x0020bd5f` |

Command hex dump:
```
16 28
18 03 16 d2
0266f2ae 0032e064 0000091d
0020bd5a 0020bd5b 0020bd5c
0020bd5d 0020bd5e 0020bd5f
```


## See also

* [Access level](../basics.md#command-access-level)
