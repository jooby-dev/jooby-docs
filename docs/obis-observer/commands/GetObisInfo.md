# GetShortNameInfo

Request/response the information for the ShortName.
Related OBIS and profile.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x0b`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Short name](../types.md#short-name) | short name                         |

### Examples

#### get info for short name `44`:

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `1`   | `0x0b` |
| request id | `3`   | `0x03` |
| short name | `44`  | `0x2c` |

Message hex dump: `0b 03 2c`


## Response

### Format

| Size  | Type                                     | Field                              |
| ----- | ---------------------------------------- | ---------------------------------- |
| `1`   | `byte`                                   | command id = `0x0c`                |
| `1`   | `byte`                                   | command size (dynamic, `10+`)      |
| `1`   | [Request ID](../types.md#request-id)     | request/response unique identifier |
| `3-7` | [OBIS](../types.md#obis)                 | OBIS code                          |
| `6`   | [OBIS profile](../types.md#obis-profile) | OBIS profile                       |

### Examples

#### short name info for OBIS `0.9.1`:

| Field        | Value                                                                                                                                                                                 | Hex              |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id   | `12`                                                                                                                                                                                  | `0x0c`           |
| command size | `11`                                                                                                                                                                                  | `0x0b`           |
| request id   | `3`                                                                                                                                                                                   | `0x03`           |
| OBIS code    | C: `0`, D: `9`, E: `1`                                                                                                                                                                | `0x02000901`     |
| OBIS profile | capturePeriod: `344` <br> sendingPeriod: `532` <br> sendingCounter: `61` <br> contentType: `STRING` <br> sendOnChange: `0` <br> archiveProfile1: `false` <br> archiveProfile2: `true` | `0x015802143d0a` |

Message hex dump: `0c 0b 03 02 00 09 01 01 58 02 14 3d 0a`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [OBIS](../types.md#obis)
* [OBIS profile](../types.md#obis-profile)
