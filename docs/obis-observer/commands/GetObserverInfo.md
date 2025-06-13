# GetObserverInfo

Request/response the information about observer, like name, software and hardware version.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x01`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `1`   | `0x01` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `01 01 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x02`                |
| `1`  | `uint8`                              | command size (dynamic, `8+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `2`  | `uint8`                              | [software version](#version)       |
| `2`  | `uint8`                              | [protocol version](#version)       |
| `2`  | `uint8`                              | [hardware version](#version)       |
| `1+` | [String](../types.md#string)         | Name of the device                 |

### Parameters

#### version

| Size | Type    | Field                |
| ---- | ------- | -------------------- |
| `1`  | `uint8` | Major version number |
| `1`  | `uint8` | Minor version number |


### Examples

| Field            | Value                               | Hex                                                                      |
| ---------------- | ----------------------------------- | ------------------------------------------------------------------------ |
| command id       | `2`                                 | `0x02`                                                                   |
| command size     | `42`                                | `0x29`                                                                   |
| request id       | `7`                                 | `0x07`                                                                   |
| software version | `0.1`                               | `0x0001`                                                                 |
| protocol version | `0.1`                               | `0x0001`                                                                 |
| hardware version | `1.1`                               | `0x0101`                                                                 |
| name             | `Jooby Electra RM LoraWan 1D485 EU` | `0x214a6f6f627920456c656374726120524d204c6f726157616e203144343835204555` |

Message hex dump: `02 29 00 00 01 00 01 01 01 21 4a 6f 6f 62 79 20 45 6c 65 63 74 72 61 20 52 4d 20 4c 6f 72 61 57 61 6e 20 31 44 34 38 35 20 45 55`


## See also

* [Request ID](../types.md#request-id)
* [String](../types.md#string)
