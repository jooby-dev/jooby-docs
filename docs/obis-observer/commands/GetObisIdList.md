# GetObisIdList

Request/response to get the OBIS id list for the specific OBIS code and meter profile.


## Request

### Format

| Size  | Type                                             | Field                              |
| ----- | ------------------------------------------------ | ---------------------------------- |
| `1`   | `byte`                                           | command id = `0x40`                |
| `1`   | `byte`                                           | command size                       |
| `1`   | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`   | [Meter profile id](../types.md#meter-profile-id) | meter profile unique identifier    |
| `3-7` | [OBIS](../types.md#obis)                         | OBIS code                          |


### Examples

#### get OBIS id for OBIS `0.9.1`:

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
| `1`  | `byte`                               | command size (dynamic, `4+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [OBIS id](../types.md#obis-id)       | OBIS id `1`                        |
| ...  | ...                                  | ...                                |
| `1`  | [OBIS id](../types.md#obis-id)       | OBIS id `N`                        |


### Examples

#### OBIS id list for OBIS `0.9.1`:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `65`  | `0x41` |
| command size | `3`   | `0x03` |
| request id   | `7`   | `0x07` |
| OBIS id `1`  | `197` | `0xc5` |
| OBIS id `2`  | `198` | `0xc6` |

Message hex dump: `41 03 07 c5 c6`


## See also

* [Request ID](../types.md#request-id)
* [Meter profile id](../types.md#meter-profile-id)
* [OBIS](../types.md#obis)
* [OBIS id](../types.md#obis-id)
