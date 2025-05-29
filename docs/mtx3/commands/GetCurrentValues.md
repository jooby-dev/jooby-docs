# GetCurrentValues

Request/response to get current values like voltage, power, etc.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x0d` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `13`  | `0x0d` |
| command size | `0`   | `0x00` |

Command hex dump: `0d 00`


## Response

### Format

| Size | Type    | Field                                                                               |
| ---- | ------- | ----------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x0d`                                                                 |
| `1`  | `uint8` | command size = `52`                                                                 |
| `1`  | `int32` | voltage in phase `A` (`32.7.0`)                                                     |
| `1`  | `int32` | voltage in phase `B` (`52.7.0`)                                                     |
| `1`  | `int32` | voltage in phase `C` (`72.7.0`)                                                     |
| `1`  | `int32` | current in phase `A` (`31.7.0`)                                                     |
| `1`  | `int32` | current in phase `B` (`51.7.0`)                                                     |
| `1`  | `int32` | current in phase `C` (`71.7.0`)                                                     |
| `1`  | `int32` | active power in channel `A` (`1.21.7.0`)                                            |
| `1`  | `int32` | active power in channel `B` (`1.41.7.0`)                                            |
| `1`  | `int32` | active power in channel `C` (`1.61.7.0`)                                            |
| `1`  | `int32` | reactive power in channel `A` (`1.23.7.0` if `varA >= 0`; `1.24.7.0` if `varA < 0`) |
| `1`  | `int32` | reactive power in channel `B` (`1.43.7.0` if `varB >= 0`; `1.44.7.0` if `varB < 0`) |
| `1`  | `int32` | reactive power in channel `C` (`1.63.7.0` if `varC >= 0`; `1.64.7.0` if `varC < 0`) |
| `1`  | `int32` | current in neutral (`91.7.0`)                                                       |

### Examples

Default parameters:

| Field                     | Value     | Hex          |
| ------------------------- | --------- | ------------ |
| command id                | `13`      | `0x0d`       |
| command size              | `32`      | `0x34`       |
| voltage in phase          | `230000`  | `0x00038270` |
| voltage in phase          | `231000`  | `0x00038658` |
| voltage in phase          | `229000`  | `0x00037e88` |
| current in phase          | `5000`    | `0x00001388` |
| current in phase          | `4900`    | `0x00001324` |
| current in phase          | `5050`    | `0x000013ba` |
| active power in channel   | `1150000` | `0x00118c30` |
| active power in channel   | `1120000` | `0x00111700` |
| active power in channel   | `1160000` | `0x0011b340` |
| reactive power in channel | `200000`  | `0x00030d40` |
| reactive power in channel | `195000`  | `0x0002f9b8` |
| reactive power in channel | `205000`  | `0x000320c8` |
| current in neutral        | `1500`    | `0x000005dc` |

Command hex dump: `0d 34 00038270 00038658 00037e88 00001388 00001324 000013ba 00118c30 00111700 0011b340 00030d40 0002f9b8 000320c8 000005dc`


## See also

* [Access level](../basics.md#command-access-level)
