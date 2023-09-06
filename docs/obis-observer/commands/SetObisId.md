# SetObisId

Request/response to set the OBIS ID for the specific OBIS code and meter profile.


## Request

### Format

| Size  | Type                                             | Field                              |
| ----- | ------------------------------------------------ | ---------------------------------- |
| `1`   | `byte`                                           | command id = `0x42`                |
| `1`   | `byte`                                           | command size                       |
| `1`   | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`   | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`   | [OBIS ID](../types.md#obis-id)                   | OBIS unique identifier             |
| `3-7` | [OBIS](../types.md#obis)                         | OBIS code                          |

### Examples

#### set OBIS ID `44` for OBIS `0.9.1`:

| Field            | Value                  | Hex          |
| ---------------- | ---------------------- | ------------ |
| command id       | `66`                   | `0x42`       |
| command size     | `7`                    | `0x07`       |
| request id       | `4`                    | `0x04`       |
| meter profile id | `10`                   | `0x0a`       |
| OBIS ID          | `44`                   | `0x2c`       |
| OBIS code        | C: `0`, D: `9`, E: `1` | `0x02000901` |

Message hex dump: `42 07 04 0a 2c 02 00 09 01`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x43`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `67`  | `0x43` |
| command size | `2`   | `0x02` |
| request id   | `20`  | `0x14` |
| result code  | `OK`  | `0x00` |

Message hex dump: `43 02 14 00`


### Result codes:

| Result code | Description                               |
| ----------- | ----------------------------------------- |
| `0`         | Ok. The Operation was successful.         |
| `3`         | Forbidden to reassign the static OBIS ID. |
| `4`         | Obis id allocation failed.                |
| `9`         | The meter profile not found.              |


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
* [OBIS code](../types.md#obis)
* [Result code](../types.md#result-code)
