# GetDayEnergies

Uplink command to get day energies by 4 tariffs (T1-T4).

**This command can be transmitted only via Lora.**

The command access level is [UNENCRYPTED](../basics.md#command-access-level).


## Event

### Format

| Size | Type     | Field                                                              |
| ---- | -------- | ------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x78`                                                |
| `1`  | `uint8`  | command size (dynamic, max is `100`)                               |
| `2`  | `uint8`  | [packed date](../../types.md#packed-date)                          |
| `1`  | `uint8`  | [energy flags](#energy-flags)                                      |
| `1`  | `uint8`  | [tariff flags](#non-zero-energies-flags) `A+` and `A-` for tariffs |
| `4`  | `uint32` | tariff `A+` `1` day `A+`                                           |
| `4`  | `uint32` | tariff `A+` `1` day `A+R+`                                         |
| `4`  | `uint32` | tariff `A+` `1` day `A+R-`                                         |
| `4`  | `uint32` | tariff `A+` `2` day `A+`                                           |
| `4`  | `uint32` | tariff `A+` `2` day `A+R+`                                         |
| `4`  | `uint32` | tariff `A+` `2` day `A+R-`                                         |
| `4`  | `uint32` | tariff `A+` `3` day `A+`                                           |
| `4`  | `uint32` | tariff `A+` `3` day `A+R+`                                         |
| `4`  | `uint32` | tariff `A+` `3` day `A+R-`                                         |
| `4`  | `uint32` | tariff `A+` `4` day `A+`                                           |
| `4`  | `uint32` | tariff `A+` `4` day `A+R+`                                         |
| `4`  | `uint32` | tariff `A+` `4` day `A+R-`                                         |
| `4`  | `uint32` | tariff `A-` `1` day `A-`                                           |
| `4`  | `uint32` | tariff `A-` `1` day `A-R+`                                         |
| `4`  | `uint32` | tariff `A-` `1` day `A-R-`                                         |
| `4`  | `uint32` | tariff `A-` `2` day `A-`                                           |
| `4`  | `uint32` | tariff `A-` `2` day `A-R+`                                         |
| `4`  | `uint32` | tariff `A-` `2` day `A-R-`                                         |
| `4`  | `uint32` | tariff `A-` `3` day `A-`                                           |
| `4`  | `uint32` | tariff `A-` `3` day `A-R+`                                         |
| `4`  | `uint32` | tariff `A-` `3` day `A-R-`                                         |
| `4`  | `uint32` | tariff `A-` `4` day `A-`                                           |
| `4`  | `uint32` | tariff `A-` `4` day `A-R+`                                         |
| `4`  | `uint32` | tariff `A-` `4` day `A-R-`                                         |

### Parameters

#### **energy flags**

| Bit number | Name         | Description                                    |
| ---------- | ------------ | ---------------------------------------------- |
| `0`        | `ACTIVE`     | active energy (`A+`)                           |
| `1`        | `VARI`       | positive (inductive) reactive energy (`A+R+`)  |
| `2`        | `VARE`       | negative (capacitive) reactive energy (`A+R-`) |
| `3`        | `ACTIVE_EXP` | active energy (`A-`)                           |
| `4`        | `VARI_EXP`   | positive (inductive) reactive energy (`A-R+`)  |
| `5`        | `VARE_EXP`   | negative (capacitive) reactive energy (`A-R-`) |

#### **tariff flags**

Bit field determines non-zero energies by tariff.
If the data for a tariff is `0` they are not transmitted, and the corresponding bit in this field will be reset to `0`.

| Bit number | Energy type | Tariff |
| ---------- | ----------- | ------ |
| `0`        | `A+`        | `1`    |
| `1`        | `A+`        | `2`    |
| `2`        | `A+`        | `3`    |
| `3`        | `A+`        | `4`    |
| `4`        | `A-`        | `1`    |
| `5`        | `A-`        | `2`    |
| `6`        | `A-`        | `3`    |
| `7`        | `A-`        | `4`    |

### Examples

| Field         | Value                               | Bits                  | Hex      |
| ------------- | ----------------------------------- | --------------------- | -------- |
| command id    | `120`                               |                       | `0x78`   |
| command size  | `12`                                |                       | `0x0c`   |
| packed date   | year: `2021`, month: `2`, date: `3` | `0010 1010 0100 0011` | `0x2a43` |
| energy flags  | `A+` and `A-R+`                     | `0001 0001`           | `0x11`   |
| tariff flags  | `A+` `T1` and `A-` `T1`             | `0001 0001`           | `0x11`   |
| energy `A+`   | `4096`                              |                       | `0x1000` |
| energy `A-R+` | `8192`                              |                       | `0x2000` |

Command hex dump: `78 0c 2a 43 11 11 00 00 10 00 00 00 20 00`


## See also

* [Access level](../basics.md#command-access-level)
* [Packed date](../../types.md#packed-date)
