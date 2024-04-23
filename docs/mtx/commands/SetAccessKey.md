# SetAccessKey

Request/response to set the device access key.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                 |
| ---- | ------- | ----------------------------------------------------- |
| `1`  | `uint8` | command id = `0x09`                                   |
| `1`  | `uint8` | command size = `17`                                   |
| `1`  | `uint8` | key [access level](../basics.md#command-access-level) |
| `16` | `uint8` | key data                                              |

### Examples

Set the default key for `READ_ONLY` access level:

| Field        | Value | Hex                                  |
| ------------ | ----- | ------------------------------------ |
| command id   | `9`   | `0x09`                               |
| command size | `17`  | `0x11`                               |
| access level | `3`   | `0x03`                               |
| key data     |       | `0x00010203040506070809101112131415` |

Message hex dump: `09 11 03 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x09` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `9`   | `0x09` |
| command size | `0`   | `0x00` |

Message hex dump: `09 00`


## See also

* [Access level](../basics.md#command-access-level)
