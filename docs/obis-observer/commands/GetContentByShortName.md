# GetContentByShortName

Request/response to get the OBIS code content from the metering device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x17`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Short name](../types.md#short-name) | short name                         |

### Examples

#### get content for short name `50`:

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `23`  | `0x17` |
| request id | `121` | `0x79` |
| short name | `50`  | `0x32` |

Message hex dump: `17 79 32`


## Response with float content

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x18`                        |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `4`  | `float32`                            | OBIS code content from the metering device |

### Examples

| Field      | Value    | Hex          |
| ---------- | -------- | ------------ |
| command id | `24`     | `0x18`       |
| request id | `121`    | `0x79`       |
| content    | `344.23` | `0x43ac1d71` |

Message hex dump: `18 79 43 ac 1d 71`


## Response with string content

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x19`                        |
| `1`  | `byte`                               | command size (dynamic, `3+`)               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `1+` | [String](../types.md#string)         | OBIS code content from the metering device |

### Examples

| Field        | Value          | Hex                            |
| ------------ | -------------- | ------------------------------ |
| command id   | `25`           | `0x19`                         |
| command size | `14`           | `0x0e`                         |
| request id   | `121`          | `0x79`                         |
| content      | `Total energy` | `0x0c546f74616c20656e65726779` |

Message hex dump: `19 0e 79 0c 54 6f 74 61 6c 20 65 6e 65 72 67 79`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [String](../types.md#string)
