# RemoveObis

Request/response to remove the specific OBIS from service.


## Request

### Format

| Size | Type                                             | Field                              |
| ---- | ------------------------------------------------ | ---------------------------------- |
| `1`  | `byte`                                           | command id = `0x44`                |
| `1`  | `byte`                                           | command size                       |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | meter profile unique identifier    |
| `1`  | [OBIS ID](../types.md#obis-id)                   | OBIS unique identifier             |

### Examples

#### remove profile for OBIS ID `28`:

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `68`  | `0x44` |
| command size     | `2`   | `0x02` |
| request id       | `5`   | `0x05` |
| meter profile id | `4`   | `0x04` |
| obis id          | `28`  | `0x1c` |


Message hex dump: `44 03 05 04 1c`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x45`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `69`  | `0x45` |
| command size | `1`   | `0x01` |
| request id   | `5`   | `0x05` |

Message hex dump: `45 01 05`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                  |
| ----------- | ---------------------------- |
| `3`         | Format error.                |
| `9`         | The meter profile not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)s
* [OBIS ID](../types.md#obis-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
