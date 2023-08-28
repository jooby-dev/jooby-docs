# GetShortNameProfile

Request/response the OBIS profile.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x09`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Short name](../types.md#short-name) | short name                         |

### Examples

#### get profile for short name `128`:

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `1`   | `0x09` |
| request id | `4`   | `0x04` |
| short name | `128` | `0x80` |

Message hex dump: `09 04 80`


## Response

### Format

| Size | Type                                     | Field                              |
| ---- | ---------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                   | command id = `0x0a`                |
| `1`  | [Request ID](../types.md#request-id)     | request/response unique identifier |
| `6`  | [OBIS profile](../types.md#obis-profile) | OBIS profile                       |

### Examples

#### profile for short name `121`:

| Field        | Value                                                                                                                                                                                 | Hex              |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id   | `10`                                                                                                                                                                                  | `0x0a`           |
| request id   | `3`                                                                                                                                                                                   | `0x03`           |
| OBIS profile | capturePeriod: `344` <br> sendingPeriod: `532` <br> sendingCounter: `61` <br> contentType: `STRING` <br> sendOnChange: `0` <br> archiveProfile1: `false` <br> archiveProfile2: `true` | `0x015802143d0a` |

Message hex dump: `0a 03 01 58 02 14 3d 0a`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [OBIS profile](../types.md#obis-profile)
