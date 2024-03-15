# SetParameter

Device parameters setup command.

The sensor confirms the execution of the command with [response](#response).


## Request

### Format

| Size | Type    | Field                             |
| ---- | ------- | --------------------------------- |
| `1`  | `uint8` | command id = `0x03`               |
| `1`  | `uint8` | command size  (dynamic, `2+`)     |
| `1`  | `uint8` | [parameter type](#parameter-type) |
| `1+` | `uint8` | [parameter data](#parameter-data) |

### Parameters

#### **parameter type**

See [available parameter types](../parameter-types.md).

#### **parameter data**

Type-specific structures.


## Response

It's a mandatory confirmation to [SetParameter request](./SetParameter.md#request).

### Format

| Size | Type    | Field                             |
| ---- | ------- | --------------------------------- |
| `1`  | `uint8` | command id = `0x03`               |
| `1`  | `uint8` | length = `2`                      |
| `1`  | `uint8` | [parameter type](#parameter-type) |
| `1`  | `uint8` | [status](#status)                 |

### Parameters

#### **parameter type**

See [available parameter types](../parameter-types.md).

#### **status**

`1` - parameter setup was successful <br>
`0` - parameter setting failed, parameter was not changed

### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `3`   | `0x03` |
| command size | `2`   | `0x02` |
| type         | `5`   | `0x05` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `03 02 05 01 50`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `3`   | `0x03` |
| command size | `2`   | `0x02` |
| type         | `5`   | `0x05` |
| status       | `0`   | `0x00` |

Message hex dump with LRC: `03 02 05 00 51`
