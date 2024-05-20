# GetRatePlanInfo

Request/response to get device rate plan information.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                              |
| ---- | ------- | ------------------------------------------------------------------ |
| `1`  | `uint8` | command id = `0x2c`                                                |
| `1`  | `uint8` | command size = `1`                                                 |
| `1`  | `uint8` | tariff table identifier <br/> (`0` - table `A+`, `1` – table `A-`) |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `44`  | `0x2c` |
| command size | `5`   | `0x05` |
| tariff table | `A-`  | `0x01` |

Message hex dump: `2c 05 01`


## Response

### Format

| Size | Type     | Field                                                                                                |
| ---- | -------- | ---------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x2c`                                                                                  |
| `1`  | `uint8`  | command size = `23`                                                                                  |
| `1`  | `uint8`  | tariff table identifier <br/> (`0` - table `A+`, `1` – table `A-`)                                   |
| `1`  | `uint32` | active plan: rate plan unique identifier                                                             |
| `1`  | `uint8`  | active plan: indicates the state of this tariff plan (`1` - tariff table is valid, `0` - not valid)  |
| `1`  | `uint8`  | active plan: activation year (number of years after `2000`)                                          |
| `1`  | `uint8`  | active plan: activation month (`1` - January ... `12` - December)                                    |
| `1`  | `uint8`  | active plan: activation date                                                                         |
| `1`  | `uint8`  | active plan: the number of special days in the tariff table (max `26`)                               |
| `1`  | `uint8`  | active plan: the number of seasons in the tariff table (max `14`)                                    |
| `1`  | `uint8`  | active plan: the number of days in the tariff table (max `32`)                                       |
| `1`  | `uint32` | passive plan: rate plan unique identifier                                                            |
| `1`  | `uint8`  | passive plan: indicates the state of this tariff plan (`1` - tariff table is valid, `0` - not valid) |
| `1`  | `uint8`  | passive plan: activation year (number of years after `2000`)                                         |
| `1`  | `uint8`  | passive plan: activation month (`1` - January ... `12` - December)                                   |
| `1`  | `uint8`  | passive plan: activation date                                                                        |
| `1`  | `uint8`  | passive plan: the number of special days in the tariff table (max `26`)                              |
| `1`  | `uint8`  | passive plan: the number of seasons in the tariff table (max `14`)                                   |
| `1`  | `uint8`  | passive plan: the number of days in the tariff table (max `32`)                                      |

### Examples

Activate `A+` table for plan id `1` at `2024.02.19`:

| Field                        | Value                         | Hex          |
| ---------------------------- | ----------------------------- | ------------ |
| command id                   | `19`                          | `0x2c`       |
| command size                 | `23`                          | `0x17`       |
| tariff table                 | `A-`                          | `0x01`       |
| active plan rate id          | `1`                           | `0x00000001` |
| active plan tariff state     | `valid`                       | `0x01`       |
| active plan year             | `24` (`2000` + `24` = `2024`) | `0x18`       |
| active plan month            | `2` (February)                | `0x02`       |
| active plan date             | `19`                          | `0x13`       |
| active plan special days     | `6`                           | `0x06`       |
| active plan season profiles  | `7`                           | `0x07`       |
| active plan day profiles     | `8`                           | `0x08`       |
| passive plan rate id         | `1`                           | `0x00000001` |
| passive plan tariff state    | `invalid`                     | `0x00`       |
| passive plan year            | `24` (`2000` + `24` = `2024`) | `0x18`       |
| passive plan month           | `3` (March)                   | `0x03`       |
| passive plan date            | `18`                          | `0x12`       |
| passive plan special days    | `4`                           | `0x04`       |
| passive plan season profiles | `2`                           | `0x02`       |
| passive plan day profiles    | `3`                           | `0x03`       |

Message hex dump: `2c 17 01  00 00 00 01 01 18 02 13 06 07 08  00 00 00 01 00 18 03 12 04 02 03`


## See also

* [Access level](../basics.md#command-access-level)
