# SetSingleMode

Request to set the single or multi mode of the observer device.


## Request

### Format

| Size | Type                                 | Field                                             |
| ---- | ------------------------------------ | ------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x0b`                               |
| `1`  | `uint8`                              | command size                                      |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                |
| `1`  | `uint8`                              | Single mode: <br/> `0` - multi <br/> `1` - single |


### Examples

#### get profile for OBIS ID `128`:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `1`   | `0x0b` |
| command size | `2`   | `0x02` |
| request id   | `4`   | `0x04` |
| single mode  | `1`   | `0x01` |

Message hex dump: `0b 02 04 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x0c`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `12`  | `0x0c` |
| command size | `1`   | `0x01` |
| request id   | `156` | `0x9c` |

Message hex dump: `0c 01 9c`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### result codes:

| Result code | Description                       |
| ----------- | --------------------------------- |
| `3`         | Format error.                     |
| `13`        | The multi meter mode unsupported. |


## See also

* [Request ID](../types.md#request-id)
* [Single mode](../single-mode.md)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
