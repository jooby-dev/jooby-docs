# GetExtendedCurrentValues

Request/response to get the temperature, supply frequency, etc.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x3a` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `58`  | `0x3a` |
| command size | `0`   | `0x00` |

Command hex dump: `3a 00`


## Response

### Format

| Size | Type     | Field                                          |
| ---- | -------- | ---------------------------------------------- |
| `1`  | `uint8`  | command id = `0x3a`                            |
| `1`  | `uint8`  | command size = `40`                            |
| `2`  | `int16`  | temperature                                    |
| `2`  | `uint16` | supply frequency                               |
| `4`  | `int32`  | phase angle between phase `A` and `B` voltages |
| `4`  | `int32`  | phase angle between phase `B` and `C` voltages |
| `2`  | `int16`  | power factor (`cos φ`) of phase `A`            |
| `2`  | `int16`  | power factor (`cos φ`) of phase `B`            |
| `2`  | `int16`  | power factor (`cos φ`) of phase `C`            |
| `2`  | `int16`  | power factor (`cos φ`) of all phases           |
| `4`  | `uint32` | apparent power of phase `A`                    |
| `4`  | `uint32` | apparent power of phase `B`                    |
| `4`  | `uint32` | apparent power of phase `C`                    |
| `4`  | `uint32` | apparent power of all phases                   |
| `2`  | `int16`  | battery voltage                                |

### Examples

| Field                                          | Value   | Hex          |
| ---------------------------------------------- | ------- | ------------ |
| command id                                     | `58`    | `0x3a`       |
| command size                                   | `28`    | `0x40`       |
| temperature                                    | `15`    | `0x000f`     |
| supply frequency                               | `500`   | `0x01f4`     |
| phase angle between phase `A` and `B` voltages | `120`   | `0x00000078` |
| phase angle between phase `B` and `C` voltages | `120`   | `0x00000078` |
| power factor (`cos φ`) of phase `A`            | `0.97`  | `0x0061`     |
| power factor (`cos φ`) of phase `B`            | `0.95`  | `0x005f`     |
| power factor (`cos φ`) of phase `C`            | `0.96`  | `0x0060`     |
| power factor (`cos φ`) of all phases           | `0.96`  | `0x0060`     |
| apparent power of phase `A`                    | `3600`  | `0x00000e10` |
| apparent power of phase `B`                    | `3500`  | `0x00000dac` |
| apparent power of phase `C`                    | `3550`  | `0x00000dde` |
| apparent power of all phases                   | `10650` | `0x0000299a` |
| battery voltage                                | `37`    | `0x0025`     |

Command hex dump: `3a 28 000f 01f4 00000078 00000078 0061 005f 0060 00000e10 00000dac 00000dde 0000299a 0025`


## See also

* [Access level](../basics.md#command-access-level)
