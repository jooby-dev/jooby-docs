# GetHalfHourDemandVareExport

Request/response to get reactive energy (`A-R-`) in half hours by date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x55`                           |
| `1`  | `uint8` | command size = `3`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |

### Examples

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `85`                          | `0x55` |
| command size | `3`                           | `0x03` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |
| month        | `2` (February)                | `0x02` |
| date         | `19`                          | `0x13` |

Command hex dump: `55 03 18 02 13`


## Response

### Format

#### case #1

| Size | Type     | Field                                                                 |
| ---- | -------- | --------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x55`                                                   |
| `1`  | `uint8`  | command size = `27`                                                   |
| `1`  | `uint8`  | year (number of years after `2000`)                                   |
| `1`  | `uint8`  | month (`1` - January ... `12` - December)                             |
| `1`  | `uint8`  | date (month day number which starts from `1`)                         |
| `48` | `uint16` | negative (capacitive) reactive energy (`A-R-`) for a half-hour period |

#### case #2

| Size | Type     | Field                                                                  |
| ---- | -------- | ---------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x55`                                                    |
| `1`  | `uint8`  | command size = `27`                                                    |
| `1`  | `uint8`  | year (number of years after `2000`)                                    |
| `1`  | `uint8`  | month (`1` - January ... `12` - December)                              |
| `1`  | `uint8`  | date (month day number which starts from `1`)                          |
| `48` | `uint16` | negative (capacitive) reactive energy (`A-R-`) for a half-hour period  |
| `4`  | `uint16` | load data for the additional hour during the transition to winter time |
| `1`  | `uint8`  | additional hour number                                                 |

### Parameters

#### **active energy**

The value `0xffff` means no data is provided.<br>

### Examples

#### case #1

| Field        | Value                         | Hex       |
| ------------ | ----------------------------- | --------- |
| command id   | `85`                          | `0x55`    |
| command size | `99`                          | `0x63`    |
| year         | `24` (`2000` + `24` = `2024`) | `0x18`    |
| month        | `2` (February)                | `0x02`    |
| date         | `19`                          | `0x13`    |
| energy `#0`  | `1111`                        | `0x0457`  |
| energy `#1`  | `1222`                        | `0x04c6`  |
| energy `#2`  | `1333`                        | `0x0535`  |
| energy `#3`  | `1444`                        | `0x05a4`  |
| energy `#4`  | `1555`                        | `0x0613`  |
| energy `#5`  | `1666`                        | `0x0682`  |
| energy `#6`  | `1777`                        | `0x06f1`  |
| energy `#7`  | `1888`                        | `0x0760`  |
| energy `#8`  | `1999`                        | `0x07cf`  |
| energy `#9`  | `2000`                        | `0x07d0`  |
| energy `#10` | `2111`                        | `0x083f`  |
| energy `#11` | `2222`                        | `0x08ae`  |
| energy `#12` | `2333`                        | `0x091d`  |
| energy `#13` | `2444`                        | `0x098c`  |
| energy `#14` | `2555`                        | `0x09fb`  |
| energy `#15` | `2666`                        | `0x0a6a`  |
| energy `#16` | `2777`                        | `0x0ad9`  |
| energy `#17` | `2888`                        | `0x0b48`  |
| energy `#18` | `2999`                        | `0x0bb7`  |
| energy `#19` | `3000`                        | `0x0bb8`  |
| energy `#20` | `3111`                        | `0x0c27`  |
| energy `#21` | `3222`                        | `0x0c96`  |
| energy `#22` | `3333`                        | `0x0d05`  |
| energy `#23` | `3444`                        | `0x0d74`  |
| energy `#24` | `3555`                        | `0x0de3`  |
| energy `#25` | `3666`                        | `0x0e52`  |
| energy `#26` | `3777`                        | `0x0ec1`  |
| energy `#27` | `3888`                        | `0x0f30`  |
| energy `#28` | `3999`                        | `0x0f9f`  |
| energy `#29` | `4000`                        | `0x0fa0`  |
| energy `#30` | `4111`                        | `0x100f`  |
| energy `#31` | `4222`                        | `0x107e`  |
| energy `#32` | `4333`                        | `0x10ed`  |
| energy `#33` | `4444`                        | `0x115c`  |
| energy `#34` | `4555`                        | `0x11cb`  |
| energy `#35` | `4666`                        | `0x123a`  |
| energy `#36` | `4777`                        | `0x12a9`  |
| energy `#37` | `4888`                        | `0x1318`  |
| energy `#38` | `4999`                        | `0x1387`  |
| energy `#39` | `5000`                        | `0x1388`  |
| energy `#40` | `5222`                        | `0x1466`  |
| energy `#41` | `5333`                        | `0x14d5`  |
| energy `#42` | `undefined`                   | `0xffff`  |
| energy `#43` | `undefined`                   | `0xffff`  |
| energy `#44` | `5666`                        | `0x1622`  |
| energy `#45` | `5777`                        | `0x1691`  |
| energy `#46` | `5888`                        | `0x1700`  |
| energy `#47` | `5999`                        | `0x176f ` |

Command hex dump:
```
55 63
18 02 13
0457 04c6 0535 05a4 0613 0682 06f1 0760 07cf 07d0 083f 08ae
091d 098c 09fb 0a6a 0ad9 0b48 0bb7 0bb8 0c27 0c96 0d05 0d74
0de3 0e52 0ec1 0f30 0f9f 0fa0 100f 107e 10ed 115c 11cb 123a
12a9 1318 1387 1388 1466 14d5 ffff ffff 1622 1691 1700 176f
```

#### case #2

| Field                       | Value                         | Hex      |
| --------------------------- | ----------------------------- | -------- |
| command id                  | `85`                          | `0x55`   |
| command size                | `104`                         | `0x68`   |
| year                        | `24` (`2000` + `24` = `2024`) | `0x18`   |
| month                       | `2` (February)                | `0x02`   |
| date                        | `19`                          | `0x13`   |
| energy `#0`                 | `1111`                        | `0x0457` |
| energy `#1`                 | `1222`                        | `0x04c6` |
| energy `#2`                 | `1333`                        | `0x0535` |
| energy `#3`                 | `1444`                        | `0x05a4` |
| energy `#4`                 | `1555`                        | `0x0613` |
| energy `#5`                 | `1666`                        | `0x0682` |
| energy `#6`                 | `1777`                        | `0x06f1` |
| energy `#7`                 | `1888`                        | `0x0760` |
| energy `#8`                 | `1999`                        | `0x07cf` |
| energy `#9`                 | `2000`                        | `0x07d0` |
| energy `#10`                | `2111`                        | `0x083f` |
| energy `#11`                | `2222`                        | `0x08ae` |
| energy `#12`                | `2333`                        | `0x091d` |
| energy `#13`                | `2444`                        | `0x098c` |
| energy `#14`                | `2555`                        | `0x09fb` |
| energy `#15`                | `2666`                        | `0x0a6a` |
| energy `#16`                | `2777`                        | `0x0ad9` |
| energy `#17`                | `2888`                        | `0x0b48` |
| energy `#18`                | `2999`                        | `0x0bb7` |
| energy `#19`                | `3000`                        | `0x0bb8` |
| energy `#20`                | `3111`                        | `0x0c27` |
| energy `#21`                | `3222`                        | `0x0c96` |
| energy `#22`                | `3333`                        | `0x0d05` |
| energy `#23`                | `3444`                        | `0x0d74` |
| energy `#24`                | `3555`                        | `0x0de3` |
| energy `#25`                | `3666`                        | `0x0e52` |
| energy `#26`                | `3777`                        | `0x0ec1` |
| energy `#27`                | `3888`                        | `0x0f30` |
| energy `#28`                | `3999`                        | `0x0f9f` |
| energy `#29`                | `4000`                        | `0x0fa0` |
| energy `#30`                | `4111`                        | `0x100f` |
| energy `#31`                | `4222`                        | `0x107e` |
| energy `#32`                | `4333`                        | `0x10ed` |
| energy `#33`                | `4444`                        | `0x115c` |
| energy `#34`                | `4555`                        | `0x11cb` |
| energy `#35`                | `4666`                        | `0x123a` |
| energy `#36`                | `4777`                        | `0x12a9` |
| energy `#37`                | `4888`                        | `0x1318` |
| energy `#38`                | `4999`                        | `0x1387` |
| energy `#39`                | `5000`                        | `0x1388` |
| energy `#40`                | `5222`                        | `0x1466` |
| energy `#41`                | `5333`                        | `0x14d5` |
| energy `#42`                | `5444`                        | `0x1544` |
| energy `#43`                | `5555`                        | `0x15b3` |
| energy `#44`                | `5666`                        | `0x1622` |
| energy `#45`                | `5777`                        | `0x1691` |
| energy `#46`                | `5888`                        | `0x1700` |
| energy `#47`                | `5999`                        | `0x176f` |
| additional hour energy `#0` | `6000`                        | `0x1770` |
| additional hour energy `#1` | `6111`                        | `0x17df` |
| hour                        | `3`                           | `0x03`   |

Command hex dump:
```
55 68
18 02 13
0457 04c6 0535 05a4 0613 0682 06f1 0760 07cf 07d0 083f 08ae
091d 098c 09fb 0a6a 0ad9 0b48 0bb7 0bb8 0c27 0c96 0d05 0d74
0de3 0e52 0ec1 0f30 0f9f 0fa0 100f 107e 10ed 115c 11cb 123a
12a9 1318 1387 1388 1466 14d5 1544 15b3 1622 1691 1700 176f
1770 17df
03
```


## See also

* [Access level](../basics.md#command-access-level)
