# AddMeterProfile

Request/response to add the meter profile.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x60`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |


### Examples

#### add meter profile with id `32`:

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `96`  | `0x60` |
| command size     | `2`   | `0x02` |
| request id       | `3`   | `0x03` |
| meter profile id | `32`  | `0x20` |

Message hex dump: `60 02 03 20`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x61`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `97`  | `0x61` |
| command size | `2`   | `0x02` |
| request id   | `3`   | `0x03` |
| result code  | `OK`  | `0x00` |

Message hex dump: `61 02 03 00`


### Result codes:

| Result code | Description                                      |
| ----------- | ------------------------------------------------ |
| `0`         | Ok. The Operation was successful.                |
| `2`         | Wrong arguments. Can't use `0xff` as profile id. |
| `8`         | Meter profile allocation failed.                 |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Meter profile ID](../types.md#meter-profile-id)
