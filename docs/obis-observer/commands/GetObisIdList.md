# GetObisIdList

Request/response to get the OBIS ID list for the specific OBIS code and meter profile.


## Request

### Format

| Size  | Type                                             | Mandatory/optional | Field                              |
| ----- | ------------------------------------------------ | ------------------ | ---------------------------------- |
| `1`   | `byte`                                           | mandatory          | command id = `0x40`                |
| `1`   | `byte`                                           | mandatory          | command size                       |
| `1`   | [Request ID](../types.md#request-id)             | mandatory          | request/response unique identifier |
| `1`   | [Meter profile ID](../types.md#meter-profile-id) | mandatory          | meter profile unique identifier    |
| `3-7` | [OBIS](../types.md#obis)                         | optional           | OBIS code                          |


### Examples

#### get OBIS ID list:

| Field            | Value                  | Hex          |
| ---------------- | ---------------------- | ------------ |
| command id       | `64`                   | `0x40`       |
| command size     | `2`                    | `0x06`       |
| request id       | `3`                    | `0x03`       |
| meter profile id | `10`                   | `0x0a`       |

Message hex dump: `40 02 03 0a`

#### get OBIS ID list for OBIS `0.9.1`:

| Field            | Value                  | Hex          |
| ---------------- | ---------------------- | ------------ |
| command id       | `64`                   | `0x40`       |
| command size     | `6`                    | `0x06`       |
| request id       | `3`                    | `0x03`       |
| meter profile id | `10`                   | `0x0a`       |
| OBIS code        | C: `0`, D: `9`, E: `1` | `0x02000901` |

Message hex dump: `40 06 03 0a 02 00 09 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x41`                |
| `1`  | `byte`                               | command size (dynamic, `2+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | is list completed                  |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                        |
| ...  | ...                                  | ...                                |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `N`                        |


### Examples

#### OBIS ID list for OBIS `0.9.1`:

| Field             | Value | Hex    |
| ----------------- | ----- | ------ |
| command id        | `65`  | `0x41` |
| command size      | `4`   | `0x04` |
| request id        | `7`   | `0x07` |
| is list completed | `1`   | `0x01` |
| OBIS ID `1`       | `197` | `0xc5` |
| OBIS ID `2`       | `198` | `0xc6` |

Message hex dump: `41 04 07 01 c5 c6`


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS](../types.md#obis)
* [OBIS ID](../types.md#obis-id)
