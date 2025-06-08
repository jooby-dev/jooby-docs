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

| Size | Type    | Field                                            |
| ---- | ------- | ------------------------------------------------ |
| `1`  | `uint8` | command id = `0x04`                              |
| `1`  | `uint8` | command size = `9`                               |
| `8`  | `uint8` | device type (as string, e.g. `0012164721b3172c`) |
| `1`  | `uint8` | data 2                                           |

### Parameters

#### **device type descriptor**

Bit mask:

| Name                 | Bit | Description                                              |
| -------------------- | --- | -------------------------------------------------------- |
| `G_TYPE`       | `0` | `0` - meter type `A`<br>`1` - meter type `G`             |
| `DOWNGRADED_TO_A_TYPE` | `4` | meter type `G` downgraded to meter type `A`              |
| `METER_INFO`         | `6` | meter supports command [GetMeterInfo](./GetMeterInfo.md) |

### Examples

| Field                  | Value                                                                           | Hex                  |
| ---------------------- | ------------------------------------------------------------------------------- | -------------------- |
| command id             | `4`                                                                             | `0x04`               |
| command size           | `9`                                                                             | `0x09`               |
| device type            | `0012164721b3172c`                                                              | `0x0012164721b3172c` |
| device type descriptor | `G_TYPE`: `true`<br>`DOWNGRADED_TO_A_TYPE`: `false`<br>`METER_INFO`: `true` | `0x41`               |

Command hex dump: `04 09 0012164721b3172c 41`


## See also

* [Access level](../basics.md#command-access-level)
* [GetMeterInfo](./GetMeterInfo.md)
