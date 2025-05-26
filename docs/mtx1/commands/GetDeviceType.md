# GetDeviceType

Request/response to get the device type.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x04` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `4`   | `0x04` |
| command size | `0`   | `0x00` |

Command hex dump: `04 00`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x04` |
| `1`  | `uint8` | command size = `9`  |
| `8`  | `uint8` | data 1              |
| `1`  | `uint8` | data 2              |

### Parameters

#### **data 1**

#### **data 2**


### Examples

Device type `MTX 1G05.DH.2L2-DOB4`, revision `0x0b`, meter type `G_FULL`:

| Field        | Value | Hex                  |
| ------------ | ----- | -------------------- |
| command id   | `4`   | `0x04`               |
| command size | `9`   | `0x09`               |
| data 1       |       | `0x0012164721b3172c` |
| data 2       |       | `0x11`               |

Command hex dump: `04 09 00 12 16 47 21 b3 17 2c 11`


## See also

* [Access level](../basics.md#command-access-level)
