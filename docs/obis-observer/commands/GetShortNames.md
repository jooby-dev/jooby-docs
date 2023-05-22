# GetShortNames

Request/response the short name list of the specific OBIS code.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x01`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |
| `3-7` | [OBIS](../types.md#obis)             | OBIS code                          |

### Examples

#### get short name for OBIS `0.9.1`:

| Field      | Value                  | Hex          |
| ---------- | ---------------------- | ------------ |
| command id | `1`                    | `0x01`       |
| request id | `3`                    | `0x03`       |
| OBIS code  | C: `0`, D: `9`, E: `1` | `0x02000901` |

Message hex dump: `01 03 02 00 09 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x02`                |
| `1`  | `byte`                               | command size (dynamic, `4+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Short name](../types.md#short-name) | short name `1`                     |
| ...  | ...                                  | ...                                |
| `1`  | [Short name](../types.md#short-name) | short name `N`                     |

### Examples

#### short name list for OBIS `0.9.1`:

| Field          | Value | Hex    |
| -------------- | ----- | ------ |
| command id     | `2`   | `0x02` |
| command size   | `7`   | `0x07` |
| request id     | `3`   | `0x03` |
| short name `1` | `197` | `0xc5` |
| short name `2` | `198` | `0xc6` |

Message hex dump: `02 07 03 02 00 09 01 c5 c6`


## See also

* [Request ID](../types.md#request-id)
* [OBIS](../types.md#obis)
* [Short name](../types.md#short-name)
