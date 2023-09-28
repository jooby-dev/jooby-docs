# AddObisProfile

Request/response to set up the OBIS profile for the specific OBIS ID and meter profile.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x46`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`  | [OBIS ID](../types.md#obis-id)                   | OBIS unique identifier             |
| `6`  | [OBIS profile](../types.md#obis-profile)         | OBIS profile                       |


### Examples

#### add profile for OBIS ID `32`:

| Field            | Value                                                                                                                                                                  | Hex              |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id       | `70`                                                                                                                                                                   | `0x46`           |
| command size     | `9`                                                                                                                                                                    | `0x09`           |
| request id       | `3`                                                                                                                                                                    | `0x03`           |
| meter profile id | `10`                                                                                                                                                                   | `0x0a`           |
| OBIS ID          | `32`                                                                                                                                                                   | `0x20`           |
| OBIS profile     | capturePeriod: `244` <br> sendingPeriod: `132` <br> sendingCounter: `38` <br> contentType: `AUTO` <br> sendOnChange: `1` <br> archive1: `false` <br> archive2: `false` | `0x00f400842604` |

Message hex dump: `46 09 03 0a 20 00 f4 00 84 26 04`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x47`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `71`  | `0x47` |
| command size | `1`   | `0x01` |
| request id   | `7`   | `0x07` |

Message hex dump: `47 01 07`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                     |
| ----------- | ------------------------------- |
| `3`         | Format error.                   |
| `7`         | OBIS profile allocation failed. |
| `11`        | The meter profile not found.    |


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
* [OBIS profile](../types.md#obis-profile)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
