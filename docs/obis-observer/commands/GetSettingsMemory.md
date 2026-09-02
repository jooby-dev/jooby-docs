# GetSettingsMemory

Request/response to read a block of observer settings memory.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x90`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | `uint32_be`                          | offset                             |
| `0/4`| `uint32_be`                          | size (optional)                    |

If `size` is omitted, the device uses its default block size.

### Examples

| Field        | Value | Hex          |
| ------------ | ----- | ------------ |
| command id   | `144` | `0x90`       |
| command size | `9`   | `0x09`       |
| request id   | `5`   | `0x05`       |
| offset       | `16`  | `0x00000010` |
| size         | `4`   | `0x00000004` |

Message hex dump: `90 09 05 00 00 00 10 00 00 00 04`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x91`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | `uint32_be`                          | settings memory size               |
| `4`  | `uint32_be`                          | offset                             |
| `n`  | `uint8`                              | data                               |

### Examples

| Field                | Value        | Hex          |
| -------------------- | ------------ | ------------ |
| command id           | `145`        | `0x91`       |
| command size         | `13`         | `0x0d`       |
| request id           | `2`          | `0x02`       |
| settings memory size | `10`         | `0x0000000a` |
| offset               | `2`          | `0x00000002` |
| data                 | `0, 1, 2, 3` | `00 01 02 03` |

Message hex dump: `91 0d 02 00 00 00 0a 00 00 00 02 00 01 02 03`


## See also

* [Request ID](../types.md#request-id)
