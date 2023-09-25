# RemoveObisProfile

Request/response to remove the specific OBIS profile.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x48`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`  | [OBIS ID](../types.md#obis-id)                   | OBIS unique identifier             |

### Examples

#### remove profile for OBIS ID `28`:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `72`  | `0x48` |
| command size | `2`   | `0x02` |
| request id   | `5`   | `0x05` |
| obis id      | `28`  | `0x1c` |


Message hex dump: `48 02 05 1c`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x49`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `73`  | `0x49` |
| command size | `1`   | `0x01` |
| request id   | `5`   | `0x05` |

Message hex dump: `49 01 05`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description   |
| ----------- | ------------- |
| `3`         | Format error. |


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
