# SetShortName

Request/response to set the short name for the specific OBIS code.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x03`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`   | [Short name](../types.md#short-name) | short name                         |
| `3-7` | [OBIS](../types.md#obis)             | OBIS code                          |

### Examples

#### set short name `44` for OBIS `0.9.1`:

| Field      | Value                  | Hex          |
| ---------- | ---------------------- | ------------ |
| command id | `3`                    | `0x03`       |
| request id | `4`                    | `0x04`       |
| short name | `44`                   | `0x2c`       |
| OBIS code  | C: `0`, D: `9`, E: `1` | `0x02000901` |

Message hex dump: `03 04 2c 02 00 09 01`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x04`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `4`   | `0x04` |
| request id  | `2`   | `0x02` |
| result code | `OK`  | `0x00` |

Message hex dump: `04 02 00`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [OBIS code](../types.md#obis)
* [Result code](../types.md#result-code)
