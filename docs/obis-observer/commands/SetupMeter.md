# SetupMeter

Request/response to setup the meter id, meter profile id, meter address to the meter.
A new meter will be created if it doesn't exist.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x70`                |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Meter id](../types.md#meter-id)                 | meter unique identifier            |
| `1`  | [Meter profile id](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1+` | [String](../types.md#string)                     | meter address                      |


### Examples

| Field            | Value     | Hex                  |
| ---------------- | --------- | -------------------- |
| command id       | `112`     | `0x70`               |
| command size     | `12`      | `0x0c`               |
| request id       | `121`     | `0x29`               |
| meter id         | `1`       | `0x01`               |
| meter profile id | `2`       | `0x02`               |
| meter address    | `2345432` | `0x0732333435343332` |

Message hex dump: `70 0c 29 01 02 07 32 33 34 35 34 33 32`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x71`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `113` | `0x71` |
| command size | `2`   | `0x02` |
| request id   | `156` | `0x9c` |
| result code  | `0`   | `0x00` |

Message hex dump: `71 02 9c 00`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `113` | `0x71` |
| command size | `2`   | `0x02` |
| request id   | `49`  | `0x31` |
| result code  | `2`   | `0x02` |

Message hex dump: `71 02 31 02`


### Result codes:

| Result code | Description                                                                                       |
| ----------- | ------------------------------------------------------------------------------------------------- |
| `0`         | Ok. The Operation was successful.                                                                 |
| `2`         | Wrong arguments. Invalid meter id, or the meter address too big.                                  |
| `7`         | The meter id table full. Unable to add new entries.                                               |
| `10`        | The meter profile not found.                                                                      |
| `12`        | The single meter mode collision. Empty address in multi meter mode. Address in single meter mode. |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Meter id](../types.md#meter-id)
* [Meter profile id](../types.md#meter-profile-id)
