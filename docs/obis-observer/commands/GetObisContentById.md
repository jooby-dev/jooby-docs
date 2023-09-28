# GetObisContentById

Request/response to get the OBIS code content from the specific metering device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x50`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS unique identifier             |

### Examples

#### get content for OBIS ID `50`:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `80`  | `0x50` |
| command size | `3`   | `0x03` |
| request id   | `121` | `0x79` |
| meter id     | `11`  | `0x0b` |
| OBIS ID      | `50`  | `0x32` |

Message hex dump: `50 03 79 0b 32`


## Response with float content

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x51`                        |
| `1`  | `byte`                               | command size                               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `4`  | `float32`                            | OBIS code content from the metering device |

### Examples

| Field        | Value    | Hex          |
| ------------ | -------- | ------------ |
| command id   | `81`     | `0x51`       |
| command size | `5`      | `0x05`       |
| request id   | `121`    | `0x79`       |
| content      | `344.23` | `0x43ac1d71` |

Message hex dump: `51 05 79 43 ac 1d 71`


## Response with string content

### Format

| Size | Type                                 | Field                                      |
| ---- | ------------------------------------ | ------------------------------------------ |
| `1`  | `byte`                               | command id = `0x52`                        |
| `1`  | `byte`                               | command size (dynamic, `3+`)               |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier         |
| `1+` | [String](../types.md#string)         | OBIS code content from the metering device |

### Examples

| Field        | Value          | Hex                            |
| ------------ | -------------- | ------------------------------ |
| command id   | `82`           | `0x52`                         |
| command size | `14`           | `0x0e`                         |
| request id   | `121`          | `0x79`                         |
| content      | `Total energy` | `0x0c546f74616c20656e65726779` |

Message hex dump: `52 0e 79 0c 54 6f 74 61 6c 20 65 6e 65 72 67 79`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description          |
| ----------- | -------------------- |
| `3`         | Format error.        |
| `9`         | The meter not found. |


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [OBIS ID](../types.md#OBIS-id)
* [String](../types.md#string)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
