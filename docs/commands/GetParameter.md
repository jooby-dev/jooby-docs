# GetParameter

The command to read the parameter set in the sensor.

In the body of the command, you must specify the type of the parameter.
In response, the sensor will transmit the current value of the requested parameter.


## Request

### Format

| Size | Type   | Field                             |
| ---- | ------ | --------------------------------- |
| 1    | `byte` | command id = `0x04`               |
| 1    | `byte` | command size = `1`                |
| 1    | `byte` | [parameter type](#parameter-type) |

### Parameters

#### **parameter type**

See [available parameter types](../parameter-types.md).

### Examples

#### initial data:

| Field          | Value | Hex    |
| -------------- | ----- | ------ |
| command id     | `4`   | `0x04` |
| command size   | `1`   | `0x01` |
| parameter type | `23`  | `0x17` |

Message hex dump with LRC: `04 01 17 47`


## Response

It's a mandatory confirmation to [GetParameter request](./GetParameter.md#request).

### Format

| Size | Type   | Field                             |
| ---- | ------ | --------------------------------- |
| 1    | `byte` | command id = `0x04`               |
| 1    | `byte` | command size (dynamic, `2+`)      |
| 1    | `byte` | [parameter type](#parameter-type) |
| 1+   | `byte` | [parameter data](#parameter-data) |

### Parameters

#### **parameter type**

See [available parameter types](../parameter-types.md).

#### **parameter data**

Type-specific structures.

### Examples

#### initial data:

| Field             | Value  | Hex          |
| ----------------- | ------ | ------------ |
| command id        | `4`    | `0x04`       |
| command size      | `10`   | `0x0a`       |
| parameter type    | `23`   | `0x17`       |
| meter value       | `204`  | `0x000000cc` |
| pulse coefficient | `100`  | `0x82`       |
| value             | `2023` | `0x000007e7` |

Message hex dump with LRC: `04 0a 17 00 00 00 cc 82 00 00 07 e7 e2`
