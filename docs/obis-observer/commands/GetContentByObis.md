# GetContentByObis

Request/response to get the OBIS code content from the metering device.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x15`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |
| `3-7` | [OBIS](../types.md#obis)             | OBIS code                          |

### Examples

#### get content for OBIS code `0.9.1` - local time:

| Field      | Value                  | Hex             |
| ---------- | ---------------------- | --------------- |
| command id | `21`                   | `0x15`          |
| request id | `3`                    | `0x03`          |
| OBIS code  | C: `0`, D: `9`, E: `1` | `0x02 00 09 01` |

Message hex dump: `15 03 02 00 09 01`


## Response

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x16`                        |
| `1`  | `byte`                               | command size (dynamic, `3+`)               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `1+` | [String](../types.md#string)         | OBIS code content from the metering device |

### Examples

| Field        | Value      | Hex                    |
| ------------ | ---------- | ---------------------- |
| command id   | `22`       | `0x16`                 |
| command size | `10`       | `0x0a`                 |
| request id   | `2`        | `0x02`                 |
| content      | `57906635` | `0x083537393036363335` |

Message hex dump: `16 0a 02 08 35 37 39 30 36 36 33 35`


## See also

* [Request ID](../types.md#request-id)
* [OBIS](../types.md#obis)
* [String](../types.md#string)
