# GetDeviceType

Request/response to get the device type.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x04` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `4`   | `0x04` |
| command size | `0`   | `0x00` |

Command hex dump: `04 00`


## Response

### Format

| Size | Type    | Field                                             |
| ---- | ------- | ------------------------------------------------- |
| `1`  | `uint8` | command id = `0x04`                               |
| `1`  | `uint8` | command size = `9`                                |
| `8`  | `uint8` | device type (as string, e.g. `0012164721b3172c`)  |
| `1`  | `uint8` | [device type descriptor](#device-type-descriptor) |

### Parameters

#### **device type descriptor**

Bit mask:

| Name                    | Bit | Description                                                                                     |
| ----------------------- | --- | ----------------------------------------------------------------------------------------------- |
| `DOWNGRADED_TO_R_TYPE`  | `3` | meter type `G` downgraded to meter type `R`                                                     |
| `R_TYPE`                | `4` | `0` - meter type `G`<br>`1` - meter type `R`                                                    |
| `METER_INFO`            | `6` | meter supports command [GetMeterInfo](../../mtx1/commands/GetMeterInfo.md)                      |
| `REACTIVE_BY_QUADRANTS` | `7` | `0` - reactive energy as `R+R-`<br> `1` - reactive energy by quadrants (`Q1`, `Q2`, `Q3`, `Q4`) |

### Examples

| Field                                             | Value                                                                                                           | Hex                  |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | -------------------- |
| command id                                        | `4`                                                                                                             | `0x04`               |
| command size                                      | `9`                                                                                                             | `0x09`               |
| device type                                       | `0022161432712900`                                                                                              | `0x0022161432712900` |
| [device type descriptor](#device-type-descriptor) | `DOWNGRADED_TO_R_TYPE`: `false`, `R_TYPE`: `false`<br>`METER_INFO`: `false`<br>`REACTIVE_BY_QUADRANTS`: `false` | `0x00`               |

Command hex dump: `04 09 0022161432712900 00`


## See also

* [Access level](../basics.md#command-access-level)
* [GetMeterInfo](../../mtx1/commands/GetMeterInfo.md)
