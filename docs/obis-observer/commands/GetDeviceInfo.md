# GetLorawanInfo

Request/response the information about device, like name, software and hardware version.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x20`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### get device information:

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `32`  | `0x20` |
| request id | `3`   | `0x03` |

Message hex dump: `20 03`


## Response

### Format

| Size | Type                                 | Field                                           |
| ---- | ------------------------------------ | ----------------------------------------------- |
| `1`  | `byte`                               | command id = `0x21`                             |
| `1`  | `byte`                               | command size (dynamic, `6+`)                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier              |
| `2`  | `byte`                               | [software version](#version)                    |
| `2`  | `byte`                               | [hardware version](#version)                    |
| `1+` | [String](../types.md#string)         | Name of the device                              |

### Parameters

#### **version**

| Size | Type    | Field                |
| ---- | ------- | -------------------- |
| `1`  | `byte`  | Major version number |
| `1`  | `byte`  | Minor version number |


### Examples

#### Device information:

| Field                 | Value                                          | Hex                                                                      |
| --------------------- | ---------------------------------------------- | ------------------------------------------------------------------------ |
| command id            | `33`                                           | `0x21`                                                                   |
| request id            | `7`                                            | `0x07`                                                                   |
| software version      | `0.1`                                          | `0x0001`                                                                 |
| hardware version      | `1.1`                                          | `0x0101`                                                                 | 
| name                  | `Jooby Electra RM LoraWan 1D485 EU`            | `0x214a6f6f627920456c656374726120524d204c6f726157616e203144343835204555` |

Message hex dump: `21 07 00 01 01 01 21 4a 6f 6f 62 79 20 45 6c 65 63 74 72 61 20 52 4d 20 4c 6f 72 61 57 61 6e 20 31 44 34 38 35 20 45 55`


## See also

* [Request ID](../types.md#request-id)
* [String](../types.md#string)
