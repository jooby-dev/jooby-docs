# RemoveMeterProfile

Request/response to remove the specific meter profile.

## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x62`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |


### Examples

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `98`  | `0x62` |
| command size     | `2`   | `0x02` |
| request id       | `18`  | `0x12` |
| meter profile id | `2`   | `0x02` |

Message hex dump: `62 02 12 02`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x63`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `99`  | `0x63` |
| command size | `2`   | `0x02` |
| request id   | `7`   | `0x07` |
| result code  | `OK`  | `0x00` |

Message hex dump: `63 02 07 00`


### Result codes:

| Result code | Description                       |
| ----------- | --------------------------------- |
| `0`         | Ok. The Operation was successful. |
| `10`        | The meter profile not found.      |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Meter profile ID](../types.md#meter-profile-id)
