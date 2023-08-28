# GetObisProfile

Request/response to get the OBIS profile for the specific OBIS id and meter profile.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x48`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile id](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`  | [OBIS id](../types.md#obis-id)                   | OBIS unique identifier             |

### Examples

#### get profile for OBIS id `128`:

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `72`  | `0x48` |
| command size     | `3`   | `0x03` |
| request id       | `4`   | `0x04` |
| meter profile id | `8`   | `0x08` |
| OBIS id          | `128` | `0x80` |

Message hex dump: `09 03 04 08 80`


## Response

### Format

| Size | Type                                     | Field                              |
| ---- | ---------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                   | command id = `0x49`                |
| `1`  | `byte`                                   | command size                       |
| `1`  | [Request ID](../types.md#request-id)     | request/response unique identifier |
| `6`  | [OBIS profile](../types.md#obis-profile) | OBIS profile                       |


### Examples

#### profile for OBIS id `121`:

| Field        | Value                                                                                                                                                                                 | Hex              |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id   | `73`                                                                                                                                                                                  | `0x49`           |
| command size | `7`                                                                                                                                                                                   | `0x07`           |
| request id   | `3`                                                                                                                                                                                   | `0x03`           |
| OBIS profile | capturePeriod: `344` <br> sendingPeriod: `532` <br> sendingCounter: `61` <br> contentType: `STRING` <br> sendOnChange: `0` <br> archiveProfile1: `false` <br> archiveProfile2: `true` | `0x015802143d0a` |

Message hex dump: `49 07 03 01 58 02 14 3d 0a`


## See also

* [Request ID](../types.md#request-id)
* [Meter profile id](../types.md#meter-profile-id)
* [OBIS id](../types.md#obis-id)
* [OBIS profile](../types.md#obis-profile)
