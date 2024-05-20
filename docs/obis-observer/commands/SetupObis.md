# SetObisId

Request/response to set the OBIS ID and OBIS profile for the specific OBIS code and meter profile.


## Request

### Format

| Size  | Type                                             | Mandatory/optional | Field                              |
| ----- | ------------------------------------------------ | ------------------ | ---------------------------------- |
| `1`   | `uint8`                                          | mandatory          | command id = `0x42`                |
| `1`   | `uint8`                                          | mandatory          | command size (dynamic, 9+)         |
| `1`   | [Request ID](../types.md#request-id)             | mandatory          | request/response unique identifier |
| `1`   | [Meter profile ID](../types.md#meter-profile-id) | mandatory          | meter profile unique identifier    |
| `1`   | [OBIS ID](../types.md#obis-id)                   | mandatory          | OBIS unique identifier             |
| `6`   | [OBIS profile](../types.md#obis-profile)         | mandatory          | OBIS profile                       |
| `3-7` | [OBIS](../types.md#obis)                         | optional           | OBIS code                          |

### Examples

#### setup OBIS profile and OBIS code `0.9.1` with OBIS ID `44`:

| Field            | Value                                                                                                                                                                        | Hex              |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id       | `66`                                                                                                                                                                         | `0x42`           |
| command size     | `7`                                                                                                                                                                          | `0x07`           |
| request id       | `4`                                                                                                                                                                          | `0x04`           |
| meter profile id | `10`                                                                                                                                                                         | `0x0a`           |
| OBIS ID          | `44`                                                                                                                                                                         | `0x2c`           |
| OBIS profile     | capturePeriod: `244` <br/> sendingPeriod: `132` <br/> sendingCounter: `38` <br/> contentType: `AUTO` <br/> sendOnChange: `1` <br/> archive1: `false` <br/> archive2: `false` | `0x00f400842604` |
| OBIS code        | C: `0`, D: `9`, E: `1`                                                                                                                                                       | `0x02000901`     |

Message hex dump: `42 0d 04 0a 2c 00 f4 00 84 26 04 02 00 09 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x43`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `67`  | `0x43` |
| command size | `1`   | `0x01` |
| request id   | `20`  | `0x14` |

Message hex dump: `43 01 14`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                     |
| ----------- | ------------------------------- |
| `3`         | Format error.                   |
| `5`         | OBIS ID allocation failed.      |
| `6`         | OBIS not found.                 |
| `7`         | OBIS profile allocation failed. |
| `11`        | The meter profile not found.    |


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
* [OBIS code](../types.md#obis)
* [OBIS profile](../types.md#obis-profile)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
