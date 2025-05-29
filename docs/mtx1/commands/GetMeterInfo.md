# GetMeterInfo

Request/response to get integration period.
Same field (`operatorParameters.timeCorrectPeriod`) exists in [mtx1 operator parameters](./SetOperatorParameters.md#request) and in [mtx3 operator parameters](../../mtx3/commands/SetOperatorParameters.md#request).


The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x7a` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `122` | `0x7a` |
| command size | `0`   | `0x00` |

Command hex dump: `7a 00`


## Response

### Format

| Size | Type    | Field                                                                                                                             |
| ---- | ------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x7a`                                                                                                               |
| `1`  | `uint8` | command size = `1`                                                                                                                |
| `1`  | `uint8` | integration period for energy profiles `A+`, `A-`, voltage VA , `0`, `30` - `30`, `1`, `3`, `5`, `10`, `15`, `60` minutes (`ten`) |

### Examples

| Field              | Value | Hex    |
| ------------------ | ----- | ------ |
| command id         | `122` | `0x7a` |
| command size       | `1`   | `0x01` |
| integration period | `15`  | `0x0f` |

Command hex dump: `7a 01 0f`


## See also

* [Access level](../basics.md#command-access-level)
* [Mtx1 operator parameters](./SetOperatorParameters.md#request)
* [Mtx3 operator parameters](../../mtx3/commands/SetOperatorParameters.md#request)
*