# GetMonthMaxDemand

Request/response to get the maximum monthly power (`A+R+`, `R+`, `A+R-`) for all tariffs (`T1`-`T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x32`                       |
| `1`  | `uint8` | command size = `2`                        |
| `1`  | `uint8` | year (number of years after `2000`)       |
| `1`  | `uint8` | month (`1` - January ... `12` - December) |

### Examples

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `50`                          | `0x32` |
| command size | `2`                           | `0x02` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |
| month        | `3` (March)                   | `0x03` |

Command hex dump: `32 02 18 03`


## Response

### Format

| Size   | Type                                              | Field                                                        |
| ------ | ------------------------------------------------- | ------------------------------------------------------------ |
| `1`    | `uint8`                                           | command id = `0x32`                                          |
| `1`    | `uint8`                                           | command size = `74`                                          |
| `1`    | `uint8`                                           | year (number of years after `2000`)                          |
| `1`    | `uint8`                                           | month (`1` - January ... `12` - December)                    |
| `18*n` | [tariffEnergy](./GetDayMaxDemand.md#tariffenergy) | field set with time and energies for each tariff (`T1`-`T4`) |

> `n` - the number of tariffs.


### Examples

| Field                | Value                         | Hex          |
| -------------------- | ----------------------------- | ------------ |
| command id           | `50`                          | `0x32`       |
| command size         | `74`                          | `0x4a`       |
| year                 | `24` (`2000` + `24` = `2024`) | `0x18`       |
| month                | `3` (March)                   | `0x03`       |
| hour (`T1` start)    | `0`                           | `0x00`       |
| min                  | `10`                          | `0x0a`       |
| maximum power `P+`   | `100`                         | `0x00000064` |
| hour                 | `1`                           | `0x01`       |
| min                  | `23`                          | `0x17`       |
| maximum power `VARi` | `2000`                        | `0x000007d0` |
| hour                 | `8`                           | `0x08`       |
| min                  | `15`                          | `0x0f`       |
| maximum power `VARe` | `5555`                        | `0x000015b3` |
| hour (`T2` start)    | `2`                           | `0x02`       |
| min                  | `20`                          | `0x14`       |
| maximum power `P+`   | `1000`                        | `0x000003e8` |
| hour                 | `3`                           | `0x03`       |
| min                  | `24`                          | `0x18`       |
| maximum power `VARi` | `20000`                       | `0x00004e20` |
| hour                 | `9`                           | `0x09`       |
| min                  | `16`                          | `0x10`       |
| maximum power `VARe` | `55555`                       | `0x0000d903` |
| hour (`T3` start)    | `4`                           | `0x04`       |
| min                  | `30`                          | `0x1e`       |
| maximum power `P+`   | `10000`                       | `0x00002710` |
| hour                 | `5`                           | `0x05`       |
| min                  | `25`                          | `0x19`       |
| maximum power `VARi` | `200000`                      | `0x00030d40` |
| hour                 | `10`                          | `0x0a`       |
| min                  | `17`                          | `0x11`       |
| maximum power `VARe` | `555555`                      | `0x00087a23` |
| hour (`T4` start)    | `6`                           | `0x06`       |
| min                  | `40`                          | `0x28`       |
| maximum power `P+`   | `100000`                      | `0x000186a0` |
| hour                 | `7`                           | `0x07`       |
| min                  | `26`                          | `0x1a`       |
| maximum power `VARi` | `2000000`                     | `0x001e8480` |
| hour                 | `11`                          | `0x0b`       |
| min                  | `18`                          | `0x12`       |
| maximum power `VARe` | `5555555`                     | `0x0054c563` |

Command hex dump:
```
32 4a
18 03
00 0a 00000064 01 17 000007d0 08 0f 000015b3
02 14 000003e8 03 18 00004e20 09 10 0000d903
04 1e 00002710 05 19 00030d40 0a 11 00087a23
06 28 000186a0 07 1a 001e8480 0b 12 0054c563
```


## See also

* [Access level](../basics.md#command-access-level)
