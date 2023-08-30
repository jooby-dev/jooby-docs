# GetObisContent

Request/response to get the OBIS code content from the specific metering device.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x4c`                |
| `1`   | `byte`                               | command size                       |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`   | [Meter ID](../types.md#meter-id)     | meter unique identifier            |
| `3-7` | [OBIS](../types.md#obis)             | OBIS code                          |


### Examples

#### get content for OBIS code `0.9.1` - local time:

| Field        | Value                  | Hex          |
| ------------ | ---------------------- | ------------ |
| command id   | `76`                   | `0x4c`       |
| command size | `6`                    | `0x06`       |
| request id   | `3`                    | `0x03`       |
| meter id     | `1`                    | `0x01`       |
| OBIS code    | C: `0`, D: `9`, E: `1` | `0x02000901` |

Message hex dump: `4c 06 03 01 02 00 09 01`


## Response

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x4b`                        |
| `1`  | `byte`                               | command size (dynamic, `3+`)               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `1+` | [String](../types.md#string)         | OBIS code content from the metering device |


### Examples

| Field        | Value      | Hex                    |
| ------------ | ---------- | ---------------------- |
| command id   | `77`       | `0x4b`                 |
| command size | `10`       | `0x0a`                 |
| request id   | `2`        | `0x02`                 |
| content      | `57906635` | `0x083537393036363335` |

Message hex dump: `4b 0a 02 08 35 37 39 30 36 36 33 35`


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [OBIS](../types.md#obis)
* [String](../types.md#string)
