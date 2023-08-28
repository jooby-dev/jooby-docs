# RemoveShortNameProfile

Request/response to remove the ShortName from the management.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x07`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Short name](../types.md#short-name) | short name                         |

### Examples

#### remove profile for short name `28`:

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `7`   | `0x07` |
| request id | `5`   | `0x05` |
| short name | `28`  | `0x1c` |


Message hex dump: `07 05 1c`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x08`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

#### remove short name profile - not found:

| Field       | Value               | Hex    |
| ----------- | ------------------- | ------ |
| command id  | `8`                 | `0x08` |
| request id  | `5`                 | `0x05` |
| result code | `PROFILE_NOT_FOUND` | `0x05` |

Message hex dump: `08 05 05`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [Result code](../types.md#result-code)
