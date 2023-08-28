# AddShortNameProfile

Request/response to set up the OBIS profile for the specific short name.


## Request

### Format

| Size | Type                                     | Field                              |
| ---- | ---------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                   | command id = `0x05`                |
| `1`  | [Request ID](../types.md#request-id)     | request/response unique identifier |
| `1`  | [Short name](../types.md#short-name)     | short name                         |
| `6`  | [OBIS profile](../types.md#obis-profile) | OBIS profile                       |

### Examples

#### add profile for short name `32`:

| Field        | Value                                                                                                                                                                                | Hex              |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| command id   | `5`                                                                                                                                                                                  | `0x05`           |
| request id   | `3`                                                                                                                                                                                  | `0x03`           |
| short name   | `32`                                                                                                                                                                                 | `0x20`           |
| OBIS profile | capturePeriod: `244` <br> sendingPeriod: `132` <br> sendingCounter: `38` <br> contentType: `AUTO` <br> sendOnChange: `1` <br> archiveProfile1: `false` <br> archiveProfile2: `false` | `0x00f400842604` |

Message hex dump: `05 03 20 00 f4 00 84 26 04`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x06`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `6`   | `0x06` |
| request id  | `7`   | `0x07` |
| result code | `OK`  | `0x00` |

Message hex dump: `06 07 00`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [OBIS profile](../types.md#obis-profile)
* [Result code](../types.md#result-code)
