# PrepareRatePlan

Request/response to prepare device for rate plan application.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type     | Field                                                                                                                                                |
| ---- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x14`                                                                                                                                  |
| `1`  | `uint8`  | command size = `5`                                                                                                                                   |
| `1`  | `uint8`  | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `4`  | `uint32` | rate plan unique identifier                                                                                                                          |

### Examples

| Field        | Value       | Hex          |
| ------------ | ----------- | ------------ |
| command id   | `20`        | `0x14`       |
| command size | `5`         | `0x05`       |
| tariff table | `A+`        | `0x00`       |
| rate plan id | `987654321` | `0x3ade68b1` |

Command hex dump: `14 05 00 3a de 68 b1`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x14` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `20`  | `0x14` |
| command size | `0`   | `0x00` |

Command hex dump: `14 00`


## See also

* [Access level](../basics.md#command-access-level)
