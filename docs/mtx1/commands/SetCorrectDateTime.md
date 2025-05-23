# SetCorrectDateTime

Request/response for incremental device time correction (for a given number of seconds).

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                           |
| ---- | ------- | ------------------------------- |
| `1`  | `uint8` | command id = `0x5c`             |
| `1`  | `uint8` | command size = `2`              |
| `1`  | `int16` | number of seconds to shift time |

### Examples

Shift device time 5 seconds forward:

| Field        | Value | Hex      |
| ------------ | ----- | -------- |
| command id   | `92`  | `0x5c`   |
| command size | `2`   | `0x02`   |
| seconds      | `5`   | `0x0005` |

Message hex dump: `5c 02 00 05`

Shift device time 5 seconds backward:

| Field        | Value | Hex      |
| ------------ | ----- | -------- |
| command id   | `92`  | `0x5c`   |
| command size | `2`   | `0x02`   |
| seconds      | `-5`  | `0xfffb` |

Message hex dump: `5c 02 ff fb`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x5c` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `92`  | `0x5c` |
| command size | `0`   | `0x00` |

Message hex dump: `5c 00`


## See also

* [Access level](../basics.md#command-access-level)
