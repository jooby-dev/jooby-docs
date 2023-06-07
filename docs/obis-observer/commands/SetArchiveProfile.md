# SetArchiveProfile

Request/response to set the archive info.


## Request

### Format

| Size | Type                                 | Field                                                 |
| ---- | ------------------------------------ | ----------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x0f`                                   |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                    |
| `2`  | `uint16_be`                          | archive period for the `Archive profile 1` in minutes |
| `2`  | `uint16_be`                          | archive period for the `Archive profile 2` in minutes |

### Examples

#### set double default parameters:

| Field                    | Value  | Hex      |
| ------------------------ | ------ | -------- |
| command id               | `15`   | `0x0f`   |
| request id               | `68`   | `0x44`   |
| archive profile 1 period | `2880` | `0x0b40` |
| archive profile 2 period | `30`   | `0x001e` |

Message hex dump: `0f 44 0b 40 00 1e`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x10`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `16`  | `0x10` |
| request id  | `156` | `0x9c` |
| result code | `OK`  | `0x00` |

Message hex dump: `10 9c 00`

#### general error:

| Field       | Value     | Hex    |
| ----------- | --------- | ------ |
| command id  | `16`      | `0x10` |
| request id  | `49`      | `0x31` |
| result code | `FAILURE` | `0x01` |

Message hex dump: `10 31 01`


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
