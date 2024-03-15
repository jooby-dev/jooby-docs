# Error

The Error command is used for error indication by the OBIS observer.

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `uint8`                                | command id = `0xfe`                |
| `1`  | `uint8`                                | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `254` | `0xfe` |
| command size | `2`   | `0x02` |
| request id   | `3`   | `0x03` |
| result code  | `10`  | `0x0a` |

Message hex dump: `fe 02 03 0a`


## See also

* [Request ID](../../types.md#request-id)
* [Result code](../../types.md#result-code)
