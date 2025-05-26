# GetDayProfile

Request/response to get day profile information for the given tariff table.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                                                                                                |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x3b`                                                                                                                                  |
| `1`  | `uint8` | command size = `3`                                                                                                                                   |
| `1`  | `uint8` | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `1`  | `uint8` | day profile index in a list of all tariff days (max `32`)                                                                                            |
| `1`  | `uint8` | is it active or passive table (`0` - active, `1` - passive)                                                                                          |

### Examples

| Field        | Value   | Hex    |
| ------------ | ------- | ------ |
| command id   | `59`    | `0x3b` |
| command size | `3`     | `0x03` |
| tariff table | `A+`    | `0x00` |
| index        | `4`     | `0x04` |
| is active    | `false` | `0x01` |

Command hex dump: `3b 03 00 04 01`


## Response

### Format

| Size | Type    | Field                                    |
| ---- | ------- | ---------------------------------------- |
| `1`  | `uint8` | command id = `0x3b`                      |
| `1`  | `uint8` | command size (dynamic, `2+`, max is `8`) |
| `1+` | `uint8` | [periods](#periods)                      |

### Parameters

### periods

There may be `8` parameters max.
In case there are less parameters suffix `0xff` is used at the end.

Period format:

<table>
    <thead>
        <tr>
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
            <td colspan="2" align="center">tariff</td>
            <td>first half hour - 0 <br/> 1 - otherwise</td>
            <td colspan="5" align="center">hour</td>
        </tr>
    </tbody>
</table>

Where `tariff` - tariff number to apply for this period and `hour` - period start hour.


### Examples

#### full periods response:

| Field        | Value                                            | Hex    |
| ------------ | ------------------------------------------------ | ------ |
| command id   | `59`                                             | `0x3b` |
| command size | `8`                                              | `0x08` |
| period #1    | tariff: `0`, isFirstHalfHour: `true`, hour: `2`  | `0x10` |
| period #2    | tariff: `1`, isFirstHalfHour: `false`, hour: `3` | `0x1d` |
| period #3    | tariff: `2`, isFirstHalfHour: `true`, hour: `4`  | `0x22` |
| period #4    | tariff: `3`, isFirstHalfHour: `false`, hour: `5` | `0x2f` |
| period #5    | tariff: `0`, isFirstHalfHour: `true`, hour: `6`  | `0x30` |
| period #6    | tariff: `1`, isFirstHalfHour: `false`, hour: `7` | `0x3d` |
| period #7    | tariff: `2`, isFirstHalfHour: `false`, hour: `8` | `0x46` |
| period #8    | tariff: `3`, isFirstHalfHour: `true`, hour: `9`  | `0x4b` |

Command hex dump: `3b 08 10 1d 22 2f 30 3d 46 4b`

#### response with 4 periods:

| Field        | Value                                            | Hex    |
| ------------ | ------------------------------------------------ | ------ |
| command id   | `59`                                             | `0x3b` |
| command size | `5`                                              | `0x05` |
| period #1    | tariff: `0`, isFirstHalfHour: `true`, hour: `2`  | `0x10` |
| period #2    | tariff: `1`, isFirstHalfHour: `false`, hour: `3` | `0x1d` |
| period #3    | tariff: `2`, isFirstHalfHour: `true`, hour: `4`  | `0x22` |
| period #4    | tariff: `3`, isFirstHalfHour: `false`, hour: `5` | `0x2f` |
| final suffix |                                                  | `0xff` |

Command hex dump: `3b 05 10 1d 22 2f ff`


## See also

* [Access level](../basics.md#command-access-level)
