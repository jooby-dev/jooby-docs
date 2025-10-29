# SetDateTime

Request/response to set the device full date and time with [DST](https://en.wikipedia.org/wiki/Daylight_saving_time) flag.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x08`                           |
| `1`  | `uint8` | command size = `8`                            |
| `1`  | `uint8` | isSummerTime (`0` - winter, `1` - summer)     |
| `1`  | `uint8` | seconds                                       |
| `1`  | `uint8` | minutes                                       |
| `1`  | `uint8` | hours                                         |
| `1`  | `uint8` | day (`1` - Sunday ... `7` - Saturday)         |
| `1`  | `uint8` | date (month day number which starts from `1`) |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | year (number of years after `2000`)           |

### Examples

Time: `2024.02.19 18:31:55`:

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `8`                           | `0x08` |
| command size | `8`                           | `0x08` |
| isSummerTime | `false` (winter)              | `0x00` |
| seconds      | `55`                          | `0x37` |
| minutes      | `31`                          | `0x1f` |
| hours        | `18`                          | `0x12` |
| day          | `2` (Monday)                  | `0x02` |
| date         | `19`                          | `0x13` |
| month        | `2` (February)                | `0x02` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |

Command hex dump: `08 08 00 37 1f 12 02 13 02 18`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x08` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `8`   | `0x08` |
| command size | `0`   | `0x00` |

Command hex dump: `08 00`


## See also

* [Access level](../basics.md#command-access-level)
