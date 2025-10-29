# GetHalfHourDemandPrevious

Request/response to get the active energy (`A+`) for the previous day.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x4b` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `75`  | `0x4b` |
| command size | `0`   | `0x00` |

Command hex dump: `15 00`


## Response

Identical to [GetHalfHourDemand](./GetHalfHourDemand.md#response) response command.

### Format

#### case #1

| Size | Type     | Field                                         |
| ---- | -------- | --------------------------------------------- |
| `1`  | `uint8`  | command id = `0x4b`                           |
| `1`  | `uint8`  | command size = `27`                           |
| `1`  | `uint8`  | year (number of years after `2000`)           |
| `1`  | `uint8`  | month (`1` - January ... `12` - December)     |
| `1`  | `uint8`  | date (month day number which starts from `1`) |
| `48` | `uint16` | active energy `A+` (`1.5.x`, x=`1..4`)        |

#### case #2

| Size | Type     | Field                                                                  |
| ---- | -------- | ---------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x4b`                                                    |
| `1`  | `uint8`  | command size = `27`                                                    |
| `1`  | `uint8`  | year (number of years after `2000`)                                    |
| `1`  | `uint8`  | month (`1` - January ... `12` - December)                              |
| `1`  | `uint8`  | date (month day number which starts from `1`)                          |
| `48` | `uint16` | active energy `A+` (`1.5.x`, x=`1..4`)                                 |
| `4`  | `uint16` | load data for the additional hour during the transition to winter time |
| `1`  | `uint8`  | additional hour number                                                 |

### Parameters

#### active energy

The value `0xffff` means no data is provided.<br>
Otherwise each field holds tariff number (highest `2` bits) and energy (all other bits).

<table>
    <thead>
        <tr>
            <th>15</th>
            <th>14</th>
            <th>13</th>
            <th>12</th>
            <th>11</th>
            <th>10</th>
            <th>9</th>
            <th>8</th>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
            <th>0</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="2" align="center">tariff [<code>1..4</code>]</td>
            <td colspan="14" align="center">energy value</td>
        </tr>
    </tbody>
</table>

### Examples

#### case #1

| Field        | Value                         | Hex      |
| ------------ | ----------------------------- | -------- |
| command id   | `75`                          | `0x4b`   |
| command size | `99`                          | `0x63`   |
| year         | `24` (`2000` + `24` = `2024`) | `0x18`   |
| month        | `2` (February)                | `0x02`   |
| date         | `19`                          | `0x13`   |
| energy `#0`  | tariff `1`, energy `1111`     | `0x4457` |
| energy `#1`  | tariff `1`, energy `1222`     | `0x44c6` |
| energy `#2`  | tariff `1`, energy `1333`     | `0x4535` |
| energy `#3`  | tariff `1`, energy `1444`     | `0x45a4` |
| energy `#4`  | tariff `1`, energy `1555`     | `0x4613` |
| energy `#5`  | tariff `1`, energy `1666`     | `0x4682` |
| energy `#6`  | tariff `1`, energy `1777`     | `0x46f1` |
| energy `#7`  | tariff `1`, energy `1888`     | `0x4760` |
| energy `#8`  | tariff `1`, energy `1999`     | `0x47cf` |
| energy `#9`  | tariff `1`, energy `2000`     | `0x47d0` |
| energy `#10` | tariff `1`, energy `2111`     | `0x483f` |
| energy `#11` | tariff `1`, energy `2222`     | `0x48ae` |
| energy `#12` | tariff `1`, energy `2333`     | `0x491d` |
| energy `#13` | tariff `1`, energy `2444`     | `0x498c` |
| energy `#14` | tariff `1`, energy `2555`     | `0x49fb` |
| energy `#15` | tariff `1`, energy `2666`     | `0x4a6a` |
| energy `#16` | tariff `1`, energy `2777`     | `0x4ad9` |
| energy `#17` | tariff `1`, energy `2888`     | `0x4b48` |
| energy `#18` | tariff `1`, energy `2999`     | `0x4bb7` |
| energy `#19` | tariff `1`, energy `3000`     | `0x4bb8` |
| energy `#20` | tariff `1`, energy `3111`     | `0x4c27` |
| energy `#21` | tariff `1`, energy `3222`     | `0x4c96` |
| energy `#22` | tariff `1`, energy `3333`     | `0x4d05` |
| energy `#23` | tariff `1`, energy `3444`     | `0x4d74` |
| energy `#24` | tariff `1`, energy `3555`     | `0x4de3` |
| energy `#25` | tariff `1`, energy `3666`     | `0x4e52` |
| energy `#26` | tariff `1`, energy `3777`     | `0x4ec1` |
| energy `#27` | tariff `1`, energy `3888`     | `0x4f30` |
| energy `#28` | tariff `1`, energy `3999`     | `0x4f9f` |
| energy `#29` | tariff `1`, energy `4000`     | `0x4fa0` |
| energy `#30` | tariff `1`, energy `4111`     | `0x500f` |
| energy `#31` | tariff `1`, energy `4222`     | `0x507e` |
| energy `#32` | tariff `1`, energy `4333`     | `0x50ed` |
| energy `#33` | tariff `1`, energy `4444`     | `0x515c` |
| energy `#34` | tariff `1`, energy `4555`     | `0x51cb` |
| energy `#35` | tariff `1`, energy `4666`     | `0x523a` |
| energy `#36` | tariff `1`, energy `4777`     | `0x52a9` |
| energy `#37` | tariff `1`, energy `4888`     | `0x5318` |
| energy `#38` | tariff `1`, energy `4999`     | `0x5387` |
| energy `#39` | tariff `1`, energy `5000`     | `0x5388` |
| energy `#40` | tariff `1`, energy `5222`     | `0x5466` |
| energy `#41` | tariff `1`, energy `5333`     | `0x54d5` |
| energy `#42` | tariff `1`, energy `5444`     | `0x5544` |
| energy `#43` | tariff `1`, energy `5555`     | `0x55b3` |
| energy `#44` | tariff `1`, energy `5666`     | `0x5622` |
| energy `#45` | tariff `1`, energy `5777`     | `0x5691` |
| energy `#46` | tariff `1`, energy `5888`     | `0x5700` |
| energy `#47` | tariff `1`, energy `5999`     | `0x576f` |

Command hex dump:
```
15 1b
18 02 13
4457 44c6 4535 45a4 4613 4682 46f1 4760 47cf 47d0 483f 48ae
491d 498c 49fb 4a6a 4ad9 4b48 4bb7 4bb8 4c27 4c96 4d05 4d74
4de3 4e52 4ec1 4f30 4f9f 4fa0 500f 507e 50ed 515c 51cb 523a
52a9 5318 5387 5388 5466 54d5 5544 55b3 5622 5691 5700 576f
```

#### case #2

| Field                       | Value                         | Hex      |
| --------------------------- | ----------------------------- | -------- |
| command id                  | `75`                          | `0x4b`   |
| command size                | `104`                         | `0x68`   |
| year                        | `24` (`2000` + `24` = `2024`) | `0x18`   |
| month                       | `2` (February)                | `0x02`   |
| date                        | `19`                          | `0x13`   |
| energy `#0`                 | tariff `1`, energy `1111`     | `0x4457` |
| energy `#1`                 | tariff `1`, energy `1222`     | `0x44c6` |
| energy `#2`                 | tariff `1`, energy `1333`     | `0x4535` |
| energy `#3`                 | tariff `1`, energy `1444`     | `0x45a4` |
| energy `#4`                 | tariff `1`, energy `1555`     | `0x4613` |
| energy `#5`                 | tariff `1`, energy `1666`     | `0x4682` |
| energy `#6`                 | tariff `1`, energy `1777`     | `0x46f1` |
| energy `#7`                 | tariff `1`, energy `1888`     | `0x4760` |
| energy `#8`                 | tariff `1`, energy `1999`     | `0x47cf` |
| energy `#9`                 | tariff `1`, energy `2000`     | `0x47d0` |
| energy `#10`                | tariff `1`, energy `2111`     | `0x483f` |
| energy `#11`                | tariff `1`, energy `2222`     | `0x48ae` |
| energy `#12`                | tariff `1`, energy `2333`     | `0x491d` |
| energy `#13`                | tariff `1`, energy `2444`     | `0x498c` |
| energy `#14`                | tariff `1`, energy `2555`     | `0x49fb` |
| energy `#15`                | tariff `1`, energy `2666`     | `0x4a6a` |
| energy `#16`                | tariff `1`, energy `2777`     | `0x4ad9` |
| energy `#17`                | tariff `1`, energy `2888`     | `0x4b48` |
| energy `#18`                | tariff `1`, energy `2999`     | `0x4bb7` |
| energy `#19`                | tariff `1`, energy `3000`     | `0x4bb8` |
| energy `#20`                | tariff `1`, energy `3111`     | `0x4c27` |
| energy `#21`                | tariff `1`, energy `3222`     | `0x4c96` |
| energy `#22`                | tariff `1`, energy `3333`     | `0x4d05` |
| energy `#23`                | tariff `1`, energy `3444`     | `0x4d74` |
| energy `#24`                | tariff `1`, energy `3555`     | `0x4de3` |
| energy `#25`                | tariff `1`, energy `3666`     | `0x4e52` |
| energy `#26`                | tariff `1`, energy `3777`     | `0x4ec1` |
| energy `#27`                | tariff `1`, energy `3888`     | `0x4f30` |
| energy `#28`                | tariff `1`, energy `3999`     | `0x4f9f` |
| energy `#29`                | tariff `1`, energy `4000`     | `0x4fa0` |
| energy `#30`                | tariff `1`, energy `4111`     | `0x500f` |
| energy `#31`                | tariff `1`, energy `4222`     | `0x507e` |
| energy `#32`                | tariff `1`, energy `4333`     | `0x50ed` |
| energy `#33`                | tariff `1`, energy `4444`     | `0x515c` |
| energy `#34`                | tariff `1`, energy `4555`     | `0x51cb` |
| energy `#35`                | tariff `1`, energy `4666`     | `0x523a` |
| energy `#36`                | tariff `1`, energy `4777`     | `0x52a9` |
| energy `#37`                | tariff `1`, energy `4888`     | `0x5318` |
| energy `#38`                | tariff `1`, energy `4999`     | `0x5387` |
| energy `#39`                | tariff `1`, energy `5000`     | `0x5388` |
| energy `#40`                | tariff `1`, energy `5222`     | `0x5466` |
| energy `#41`                | tariff `1`, energy `5333`     | `0x54d5` |
| energy `#42`                | tariff `1`, energy `5444`     | `0x5544` |
| energy `#43`                | tariff `1`, energy `5555`     | `0x55b3` |
| energy `#44`                | tariff `1`, energy `5666`     | `0x5622` |
| energy `#45`                | tariff `1`, energy `5777`     | `0x5691` |
| energy `#46`                | tariff `1`, energy `5888`     | `0x5700` |
| energy `#47`                | tariff `1`, energy `5999`     | `0x576f` |
| additional hour energy `#0` | tariff `1`, energy `6000`     | `0x5770` |
| additional hour energy `#1` | tariff `1`, energy `6111`     | `0x57df` |
| hour                        | `3`                           | `0x03`   |

Command hex dump:
```
15 68
18 02 13
4457 44c6 4535 45a4 4613 4682 46f1 4760 47cf 47d0 483f 48ae
491d 498c 49fb 4a6a 4ad9 4b48 4bb7 4bb8 4c27 4c96 4d05 4d74
4de3 4e52 4ec1 4f30 4f9f 4fa0 500f 507e 50ed 515c 51cb 523a
52a9 5318 5387 5388 5466 54d5 5544 55b3 5622 5691 5700 576f
5770 57df
03
```


## See also

* [Access level](../basics.md#command-access-level)
