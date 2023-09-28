# GetObisInfo

Request/response to get the information for the specific OBIS ID and meter profile.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x4c`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`  | [OBIS ID](../types.md#obis-id)                   | OBIS unique identifier             |


### Examples

#### get info for OBIS ID `44`:

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `76`  | `0x4c` |
| command size     | `3`   | `0x03` |
| request id       | `5`   | `0x05` |
| meter profile id | `10`  | `0x0a` |
| OBIS ID          | `44`  | `0x2c` |

Message hex dump: `4c 03 05 0a 2c`


## Response

### Format

| Size  | Type                                     | Field                              |
| ----- | ---------------------------------------- | ---------------------------------- |
| `1`   | `byte`                                   | command id = `0x4d`                |
| `1`   | `byte`                                   | command size (dynamic, `10+`)      |
| `1`   | [Request ID](../types.md#request-id)     | request/response unique identifier |
| `3-7` | [OBIS](../types.md#obis)                 | OBIS code                          |
| `6`   | [OBIS profile](../types.md#obis-profile) | OBIS profile                       |


### Examples

#### OBIS ID info for OBIS `0.9.1`:

| Field        | Value                                                                                                                                                                   | Hex              |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id   | `77`                                                                                                                                                                    | `0x4d`           |
| command size | `11`                                                                                                                                                                    | `0x0b`           |
| request id   | `3`                                                                                                                                                                     | `0x03`           |
| OBIS code    | C: `0`, D: `9`, E: `1`                                                                                                                                                  | `0x02000901`     |
| OBIS profile | capturePeriod: `344` <br> sendingPeriod: `532` <br> sendingCounter: `61` <br> contentType: `STRING` <br> sendOnChange: `0` <br> archive1: `false` <br> archive2: `true` | `0x015802143d0a` |

Message hex dump: `4d 0b 03 02 00 09 01 01 58 02 14 3d 0a`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                  |
| ----------- | ---------------------------- |
| `3`         | Format error.                |
| `11`        | The meter profile not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
* [OBIS](../types.md#obis)
* [OBIS profile](../types.md#obis-profile)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
