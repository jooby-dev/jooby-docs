# GetVersion

Request/response to get device version information.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x28` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `40`  | `0x28` |
| command size | `0`   | `0x00` |

Command hex dump: `28 00`


## Response

### Format

| Size | Type    | Field                           |
| ---- | ------- | ------------------------------- |
| `1`  | `uint8` | command id = `0x28`             |
| `1`  | `uint8` | command size = `10`             |
| `10` | `uint8` | version information (as string) |

### Examples

| Field        | Value        | Hex                      |
| ------------ | ------------ | ------------------------ |
| command id   | `40`         | `0x28`                   |
| command size | `10`         | `0x0a`                   |
| version      | `104.25.003` | `0x3130342e32352e303033` |

Command hex dump: `28 0a 31 30 34 2e 32 35 2e 30 30 33`


## See also

* [Access level](../basics.md#command-access-level)
