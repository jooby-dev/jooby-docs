# GetExtendedCurrentValues

Request/response to get the temperature and supply frequency.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x3a` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `58`  | `0x3a` |
| command size | `0`   | `0x00` |

Command hex dump: `3a 00`


## Response

### Format

| Size | Type     | Field               |
| ---- | -------- | ------------------- |
| `1`  | `uint8`  | command id = `0x3a` |
| `1`  | `uint8`  | command size = `4`  |
| `4`  | `int16`  | temperature         |
| `4`  | `uint16` | supply frequency    |

### Examples

| Field            | Value | Hex      |
| ---------------- | ----- | -------- |
| command id       | `58`  | `0x3a`   |
| command size     | `4`   | `0x04`   |
| temperature      | `15`  | `0x000f` |
| supply frequency | `500` | `0x01f4` |


Command hex dump: `3a 04 000f 01f4`


## See also

* [Access level](../basics.md#command-access-level)
