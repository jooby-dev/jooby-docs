# GetMagneticFieldThreshold

Request/response to get parameters related to magnetic field detection and threshold configuration in the meter.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x6d` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `109` | `0x6d` |
| command size | `0`   | `0x00` |

Command hex dump: `6d 00`


## Response

### Format

| Size | Type     | Field                                                                            |
| ---- | -------- | -------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x6d`                                                              |
| `1`  | `uint8`  | command size = `10`                                                              |
| `2`  | `uint16` | current value of magnetic induction, millitesla                                  |
| `2`  | `uint16` | minimum magnetic induction value required to register magnetic influence (1–127) |
| `2`  | `uint16` | magnetic induction coefficient, accurate to hundredths                           |
| `4`  | `uint32` | reserved                                                                         |

### Examples

| Field                                           | Value  | Hex          |
| ----------------------------------------------- | ------ | ------------ |
| command id                                      | `109`  | `0x6d`       |
| command size                                    | `10`   | `0x0a`       |
| current value of magnetic induction, millitesla | `10`   | `0x000a`     |
| minimum magnetic induction value                | `5`    | `0x0005`     |
| magnetic induction coefficient                  | `1.23` | `007b`       |
| reserved                                        | `0`    | `0x00000000` |

Command hex dump: `6d 0a 000a 0005 007b 00000000`


## See also

* [Access level](../basics.md#command-access-level)
