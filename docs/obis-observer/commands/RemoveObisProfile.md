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

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x49`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `73`  | `0x49` |
| command size | `2`   | `0x02` |
| request id   | `5`   | `0x05` |
| result code  | `OK`  | `0x00` |

Message hex dump: `47 02 05 00`


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS ID](../types.md#obis-id)
