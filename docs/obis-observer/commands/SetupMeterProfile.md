# SetupMeterProfile

Request/response to setup the meter profile.


## Request

### Format

| Size | Type                                             | Field                                         |
| ---- | ------------------------------------------------ | --------------------------------------------- |
| `1`  | `uint8`                                          | command id = `0x60`                           |
| `1`  | `uint8`                                          | command size                                  |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier            |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier               |
| `2`  | `uint16_be`                                      | archive period for the `Archive 1` in minutes |
| `2`  | `uint16_be`                                      | archive period for the `Archive 2` in minutes |


### Examples

#### set double default parameters:

| Field            | Value  | Hex      |
| ---------------- | ------ | -------- |
| command id       | `96`   | `0x60`   |
| command size     | `5`    | `0x05`   |
| request id       | `35`   | `0x23`   |
| meter profile id | `2`    | `0x02`   |
| archive 1 period | `2880` | `0x0b40` |
| archive 2 period | `30`   | `0x001e` |

Message hex dump: `60 06 23 02 0b 40 00 1e`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x61`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `97`  | `0x61` |
| command size | `1`   | `0x01` |
| request id   | `156` | `0x9c` |

Message hex dump: `61 01 9c`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                      |
| ----------- | -------------------------------- |
| `3`         | Format error.                    |
| `10`        | Meter profile allocation failed. |

## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
