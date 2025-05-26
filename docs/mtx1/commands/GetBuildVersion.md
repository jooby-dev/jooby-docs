# GetBuildVersion

Request/response to get firmware build date and version from device.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x70` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `112` | `0x70` |
| command size | `0`   | `0x00` |

Command hex dump: `70 00`


## Response

### Format

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x70`                       |
| `1`  | `uint8` | command size = `6`                        |
| `1`  | `uint8` | date                                      |
| `1`  | `uint8` | month (`1` - January ... `12` - December) |
| `1`  | `uint8` | year (number of years after `2000`)       |
| `3`  | `uint8` | version information (as semver 3 numbers) |

### Examples

Build version: `2024.02.19/0.0.9`:

| Field        | Value                         | Hex        |
| ------------ | ----------------------------- | ---------- |
| command id   | `112`                         | `0x70`     |
| command size | `6`                           | `0x06`     |
| date         | `19`                          | `0x13`     |
| month        | `2` (February)                | `0x02`     |
| year         | `24` (`2000` + `24` = `2024`) | `0x18`     |
| version      | `0.0.9`                       | `0x000009` |

Command hex dump: `70 06 13 02 18 00 00 09`


## See also

* [Access level](../basics.md#command-access-level)
