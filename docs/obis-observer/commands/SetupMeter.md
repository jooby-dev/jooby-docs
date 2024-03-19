# SetupMeter

Request/response to setup the meter id, meter profile id, meter address to the meter.
A new meter will be created if it doesn't exist.


## Request

### Format

| Size | Type                                             | Mandatory/optional | Field                              |
| ---- | ------------------------------------------------ | ------------------ | ---------------------------------- |
| `1`  | `uint8`                                          | mandatory          | command id = `0x70`                |
| `1`  | [Request ID](../types.md#request-id)             | mandatory          | request/response unique identifier |
| `1`  | `uint8`                                          | mandatory          | command size (dynamic, `1+`)       |
| `4`  | [Meter ID](../types.md#meter-id)                 | mandatory          | meter unique identifier            |
| `1+` | [String](../types.md#string)                     | optional           | meter address                      |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | optional           | meter profile unique identifier    |


### Examples

| Field            | Value     | Hex                  |
| ---------------- | --------- | -------------------- |
| command id       | `112`     | `0x70`               |
| command size     | `14`      | `0x0e`               |
| request id       | `121`     | `0x29`               |
| meter id         | `1`       | `0x00000001`         |
| meter address    | `2345432` | `0x0732333435343332` |
| meter profile id | `2`       | `0x02`               |

Message hex dump: `70 0e 29 00 00 00 01 07 32 33 34 35 34 33 32 02`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x71`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `113` | `0x71` |
| command size | `1`   | `0x01` |
| request id   | `156` | `0x9c` |

Message hex dump: `71 01 9c`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                            |
| ----------- | -------------------------------------- |
| `3`         | Format error.                          |
| `8`         | Meter allocation failed.               |
| `11`        | The meter profile not found.           |
| `12`        | The single-multi meter mode collision. |


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
