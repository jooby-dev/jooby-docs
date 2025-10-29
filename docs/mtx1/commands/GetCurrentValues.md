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

| Size | Type    | Field                                                         |
| ---- | ------- | ------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x0d`                                           |
| `1`  | `uint8` | command size = `32`                                           |
| `4`  | `int32` | active power in A channel; A+ (`21.7.0`)                      |
| `4`  | `int32` | current in A channel (`31.7.0`)                               |
| `4`  | `int32` | voltage in A and B channels (`32.7.0`)                        |
| `4`  | `int32` | reactive power in A channel; R+ (`1.23.7.0`), R- (`1.24.7.0`) |
| `2`  | `int16` | power factor (`cos φ`) in A channel (`1.33.7.0`)              |
| `4`  | `int32` | current in B channel (`1.51.7.0`)                             |
| `4`  | `int32` | active power in B channel (`1.41.7.0`)                        |
| `4`  | `int32` | reactive power in B channel; R+ (`1.43.7.0`), R- (`1.44.7.0`) |
| `2`  | `int16` | power factor (`cos φ`) in B channel (`1.53.7.0`)              |

### Examples

Default parameters:

| Field                                | Value     | Hex          |
| ------------------------------------ | --------- | ------------ |
| command id                           | `13`      | `0x0d`       |
| command size                         | `32`      | `0x20`       |
| active power in A channel            | `2349234` | `0x0023d8b2` |
| current in A channel                 | `4061779` | `0x003dfa53` |
| voltage in A and B channels          | `302729`  | `0x00049e89` |
| reactive power in A channel          | `106789`  | `0x0001a125` |
| power factor (`cos φ`) in  A channel | `3267`    | `0x0cc3`     |
| current in B channel                 | `304779`  | `0x0004a68b` |
| active power in B channel            | `106280`  | `0x00019f28` |
| reactive power in B channel          | `107292`  | `0x0001a31c` |
| power factor (`cos φ`) in B channel  | `3767`    | `0x0eb7`     |

Command hex dump: `0d 20 0023d8b2 003dfa53 00049e89 0001a125 0cc3 0004a68b 00019f28 0001a31c 0eb7`


## See also

* [Access level](../basics.md#command-access-level)
