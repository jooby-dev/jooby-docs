# GetDayMaxPower

Uplink command to get day max power by `4` tariffs (`T1`-`T4`).

**This command can be transmitted only via Lora.**

The command access level is [UNENCRYPTED](../../basics.md#command-access-level).


## Event

### Format

| Size   | Type                        | Field                                                              |
| ------ | --------------------------- | ------------------------------------------------------------------ |
| `1`    | `uint8`                     | command id = `0x79`                                                |
| `1`    | `uint8`                     | command size (dynamic, max is `148`)                               |
| `2`    | `uint8`                     | [packed date](../../types.md#packed-date)                          |
| `1`    | `uint8`                     | [energy flags](#energy-flags)                                      |
| `1`    | `uint8`                     | [tariff flags](#non-zero-energies-flags) `A+` and `A-` for tariffs |
| `18*n` | [tariffPower](#tariffpower) | field set with time and power for each tariff `A+` (`T1`-`T4`)     |
| `18*n` | [tariffPower](#tariffpower) | field set with time and power for each tariff `A-` (`T1`-`T4`)     |

> `n` - the number of tariffs.

### Parameters

#### energy flags

| Bit number | Name         | Description                                    |
| ---------- | ------------ | ---------------------------------------------- |
| `0`        | `ACTIVE`     | active energy (`A+`)                           |
| `1`        | `VARI`       | positive (inductive) reactive energy (`A+R+`)  |
| `2`        | `VARE`       | negative (capacitive) reactive energy (`A+R-`) |
| `3`        | `ACTIVE_EXP` | active energy (`A-`)                           |
| `4`        | `VARI_EXP`   | positive (inductive) reactive energy (`A-R+`)  |
| `5`        | `VARE_EXP`   | negative (capacitive) reactive energy (`A-R-`) |

#### tariff flags

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

#### tariffPower

Each power field is linked with the previous `hour` and `minutes` fields.

| Size | Type     | Field                |
| ---- | -------- | -------------------- |
| `1`  | `uint8`  | hour                 |
| `1`  | `uint8`  | minutes              |
| `4`  | `uint32` | maximum power `A+`   |
| `1`  | `uint8`  | hour                 |
| `1`  | `uint8`  | minutes              |
| `4`  | `uint32` | maximum power `A+R+` |
| `1`  | `uint8`  | hour                 |
| `1`  | `uint8`  | minutes              |
| `4`  | `uint32` | maximum power `A+R-` |

### Examples

| Field        | Value                               | Bits                  | Hex      |
| ------------ | ----------------------------------- | --------------------- | -------- |
| command id   | `120`                               |                       | `0x79`   |
| command size | `16`                                |                       | `0x10`   |
| packed date  | year: `2021`, month: `2`, date: `3` | `0010 1010 0100 0011` | `0x2a43` |
| energy flags | `A+` and `A-R+`                     | `0001 0001`           | `0x11`   |
| tariff flags | `A+` `T3` and `A-` `T3`             | `0100 0100`           | `0x44`   |
| hours        | `2`                                 |                       | `0x02`   |
| minutes      | `3`                                 |                       | `0x03`   |
| power `A+`   | `4096`                              |                       | `0x1000` |
| hours        | `4`                                 |                       | `0x04`   |
| minutes      | `5`                                 |                       | `0x05`   |
| power `A-R+` | `8192`                              |                       | `0x2000` |

Command hex dump:

```
79 10
2a43
11 44
02 03 00001000
04 05 00002000
```


## See also

* [Access level](../../basics.md#command-access-level)
* [Packed date](../../types.md#packed-date)
