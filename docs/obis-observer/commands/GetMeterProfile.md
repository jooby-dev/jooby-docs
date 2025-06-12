# GetMeterProfile

Request/response to get the meter profile related information.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                                          | command id = `0x66`                |
| `1`  | `uint8`                                          | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |


### Examples

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `102` | `0x66` |
| command size     | `2`   | `0x02` |
| request id       | `3`   | `0x03` |
| meter profile id | `2`   | `0x02` |

Message hex dump: `66 02 03 02`


## Response

### Format

| Size | Type                                 | Field                                                            |
| ---- | ------------------------------------ | ---------------------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x67`                                              |
| `1`  | `uint8`                              | command size                                                     |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                               |
| `2`  | `uint16_be`                          | archive period for the `Archive 1` in minutes (default: `24*60`) |
| `2`  | `uint16_be`                          | archive period for the `Archive 2` in minutes (default: `15`)    |


### Examples

#### default periods:

| Field              | Value | Hex      |
| ------------------ | ----- | -------- |
| command id         | `103` | `0x67`   |
| command size       | `5`   | `0x05`   |
| request id         | `3`   | `0x03`   |
| archive `1` period | `600` | `0x0258` |
| archive `2` period | `45`  | `0x002d` |


Message hex dump: `67 05 03 02 58 00 2d`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### result codes:

| Result code | Description                  |
| ----------- | ---------------------------- |
| `3`         | Format error.                |
| `11`        | The meter profile not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
