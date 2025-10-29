# SetDayProfile

Request/response to set day profile information for the given tariff table.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                                                                                                |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x10`                                                                                                                                  |
| `1`  | `uint8` | command size (dynamic, `3+`, max is `10`)                                                                                                            |
| `1`  | `uint8` | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `1`  | `uint8` | day profile index in a list of all tariff days (max `32`)                                                                                            |
| `1+` | `uint8` | [periods](#periods)                                                                                                                                  |

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

#### full periods set:

| Field        | Value                                            | Hex    |
| ------------ | ------------------------------------------------ | ------ |
| command id   | `16`                                             | `0x10` |
| command size | `10`                                             | `0x0a` |
| tariff table | `A+`                                             | `0x00` |
| index        | `3`                                              | `0x03` |
| period #1    | tariff: `0`, isFirstHalfHour: `true`, hour: `2`  | `0x10` |
| period #2    | tariff: `1`, isFirstHalfHour: `false`, hour: `3` | `0x1d` |
| period #3    | tariff: `2`, isFirstHalfHour: `true`, hour: `4`  | `0x22` |
| period #4    | tariff: `3`, isFirstHalfHour: `false`, hour: `5` | `0x2f` |
| period #5    | tariff: `0`, isFirstHalfHour: `true`, hour: `6`  | `0x30` |
| period #6    | tariff: `1`, isFirstHalfHour: `false`, hour: `7` | `0x3d` |
| period #7    | tariff: `2`, isFirstHalfHour: `false`, hour: `8` | `0x46` |
| period #8    | tariff: `3`, isFirstHalfHour: `true`, hour: `9`  | `0x4b` |

Command hex dump: `10 0a 00 03 10 1d 22 2f 30 3d 46 4b`

#### response with 4 periods:

| Field        | Value                                            | Hex    |
| ------------ | ------------------------------------------------ | ------ |
| command id   | `16`                                             | `0x10` |
| command size | `7`                                              | `0x07` |
| tariff table | `A+`                                             | `0x00` |
| index        | `5`                                              | `0x05` |
| period #1    | tariff: `0`, isFirstHalfHour: `true`, hour: `2`  | `0x10` |
| period #2    | tariff: `1`, isFirstHalfHour: `false`, hour: `3` | `0x1d` |
| period #3    | tariff: `2`, isFirstHalfHour: `true`, hour: `4`  | `0x22` |
| period #4    | tariff: `3`, isFirstHalfHour: `false`, hour: `5` | `0x2f` |
| final suffix |                                                  | `0xff` |

Command hex dump: `10 07 00 05 10 1d 22 2f ff`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x10` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `16`  | `0x10` |
| command size | `0`   | `0x00` |

Command hex dump: `10 00`


## See also

* [Access level](../basics.md#command-access-level)
