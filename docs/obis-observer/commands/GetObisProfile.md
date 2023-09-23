# GetObisProfile

Request/response to get the OBIS profile for the specific OBIS ID and meter profile.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x4a`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`  | [OBIS ID](../types.md#obis-id)                   | OBIS unique identifier             |

### Examples

#### get profile for OBIS ID `128`:

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `74`  | `0x4a` |
| command size     | `3`   | `0x03` |
| request id       | `4`   | `0x04` |
| meter profile id | `8`   | `0x08` |
| OBIS ID          | `128` | `0x80` |

Message hex dump: `4a 03 04 08 80`


## Response

### Format

| Size | Type                                     | Field                              |
| ---- | ---------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                   | command id = `0x4b`                |
| `1`  | `byte`                                   | command size                       |
| `1`  | [Request ID](../types.md#request-id)     | request/response unique identifier |
| `6`  | [OBIS profile](../types.md#obis-profile) | OBIS profile                       |


### Examples

#### profile for OBIS ID `121`:

| Field        | Value                                                                                                                                                                   | Hex              |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| command id   | `75`                                                                                                                                                                    | `0x4b`           |
| command size | `7`                                                                                                                                                                     | `0x07`           |
| request id   | `3`                                                                                                                                                                     | `0x03`           |
| OBIS profile | capturePeriod: `344` <br> sendingPeriod: `532` <br> sendingCounter: `61` <br> contentType: `STRING` <br> sendOnChange: `0` <br> archive1: `false` <br> archive2: `true` | `0x015802143d0a` |

Message hex dump: `4b 07 03 01 58 02 14 3d 0a`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                  |
| ----------- | ---------------------------- |
| `3`         | Format error.                |
| `10`        | The meter profile not found. |


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
* [OBIS profile](../types.md#obis-profile)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
