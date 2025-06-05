# GetDemand

Request/response to get energy by selected energy type for 4 tariffs (T1-T4) for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1

| Size | Type     | Field                                                                         |
| ---- | -------- | ----------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x76`                                                           |
| `1`  | `uint8`  | command size = `8`                                                            |
| `2`  | `uint8`  | [packed date](../../types.md#packed-date)                                     |
| `1`  | `uint8`  | [demand type](#demand-type)                                                   |
| `2`  | `uint16` | index of the first requested record ([valid index range](#valid-index-range)) |
| `2`  | `uint16` | number of requested records                                                   |
| `1`  | `uint8`  | accumulation period `1/3/5/10/15/30/60`                                       |

#### request for the repeated hour during the daylight saving time change

<table>
  <thead>
    <tr>
      <th>Size</th>
      <th>Type</th>
      <th>Field</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>uint8</td>
      <td>command id = <code>0x76</code></td>
    </tr>
    <tr>
      <td>1</td>
      <td>uint8</td>
      <td>command size = <code>8</code></td>
    </tr>
    <tr>
      <td>2</td>
      <td>uint8</td>
      <td><a href="../../types.md#packed-date">packed date</a></td>
    </tr>
    <tr>
      <td>1</td>
      <td>uint8</td>
      <td><a href="#demand-type">demand type</a></td>
    </tr>
    <tr>
      <td>2</td>
      <td>uint16</td>
      <td>
        Index of the first requested record.<br/>
        <table>
          <thead>
            <tr><th>accumulation period (min)</th><th>first index</th></tr>
          </thead>
          <tbody>
            <tr><td><code>1</code></td><td><code>1440</code></td></tr>
            <tr><td><code>3</code></td><td><code>480</code></td></tr>
            <tr><td><code>5</code></td><td><code>288</code></td></tr>
            <tr><td><code>10</code></td><td><code>144</code></td></tr>
            <tr><td><code>15</code></td><td><code>96</code></td></tr>
            <tr><td><code>30</code></td><td><code>48</code></td></tr>
            <tr><td><code>60</code></td><td><code>24</code></td></tr>
          </tbody>
        </table>
      </td>
    </tr>
    <tr>
      <td>2</td>
      <td>uint16</td>
      <td>
        Number of requested records.<br/>
        <table>
          <thead>
            <tr><th>accumulation period (min)</th><th>number of records</th></tr>
          </thead>
          <tbody>
            <tr><td><code>1</code></td><td><code>61</code></td></tr>
            <tr><td><code>3</code></td><td><code>21</code></td></tr>
            <tr><td><code>5</code></td><td><code>13</code></td></tr>
            <tr><td><code>10</code></td><td><code>7</code></td></tr>
            <tr><td><code>15</code></td><td><code>5</code></td></tr>
            <tr><td><code>30</code></td><td><code>3</code></td></tr>
            <tr><td><code>60</code></td><td><code>2</code></td></tr>
          </tbody>
        </table>
      </td>
    </tr>
    <tr>
      <td>1</td>
      <td>uint8</td>
      <td>accumulation period: <code>1/3/5/10/15/30/60</code> (operatorParameters.ten)</td>
    </tr>
  </tbody>
</table>

#### Parameters

##### Demand type

| Value | Hex    | Demand type  (x=`1`..`4`)          |
| ----- | ------ | ---------------------------------- |
| `1`   | `0x01` | `A+` (`1.5.x`)                     |
| `2`   | `0x02` | `A-` (`2.5.x`)                     |
| `64`  | `0x40` | `10`-minute voltage                |
| `160` | `0xA0` | `1/3/5/10/15/30/60`-minute voltage |

##### Valid index range

| Accumulation Period (minutes) | Valid Index Range |
| ----------------------------- | ----------------- |
| `1`                           | `0 – 1440`        |
| `3`                           | `0 – 480`         |
| `5`                           | `0 – 288`         |
| `10`                          | `0 – 144`         |
| `15`                          | `0 – 96`          |
| `30`                          | `0 – 48`          |
| `60`                          | `0 – 24`          |

### Examples

#### get A+ energy

| Field                                     | Value                               | Hex      |
| ----------------------------------------- | ----------------------------------- | -------- |
| command id                                | `118`                               | `0x76`   |
| command size                              | `8`                                 | `0x08`   |
| [packed date](../../types.md#packed-date) | year: `2021`, month: `2`, date: `3` | `0x2a43` |
| [demand type](#demand-type)               | `A+`                                | `0x01`   |
| index of the first requested record       | `5`                                 | `0x0005` |
| index of the first requested record       | `10`                                | `0x000a` |
| accumulation period                       | `15`                                | `0x0f`   |

Command hex dump: `76 08 2a43 01 0005 000a 0f`


## Response

### Format

| Size | Type    | Field                                                      |
| ---- | ------- | ---------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x76`                                        |
| `1`  | `uint8` | command size = `16`                                        |
| `16` | `int32` | active energy A+ (`1.8.1` – `1.8.4`) for tariffs `T1`-`T4` |

#### response with energy type in request

| Size  | Type    | Field                                                                                                                                                                                                                                        |
| ----- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id = `0x0f`                                                                                                                                                                                                                          |
| `1`   | `uint8` | command size (dynamic, `5+`, max is `17`)                                                                                                                                                                                                    |
| `1`   | `uint8` | packed energy type with tariff flags <br/> `BIT3`-`BIT0` - energy according to OBIS code (`1` - `1.8.x`, `2` - `2.8.x`) <br/> `BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `4*n` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                                                          |

> `n` - the number of energies derived from packed energy type field.

### Examples

#### default A+ energy:

| Field        | Value      | Hex          |
| ------------ | ---------- | ------------ |
| command id   | `15`       | `0x0f`       |
| command size | `16`       | `0x10`       |
| `T1` energy  | `40301230` | `0x0266f2ae` |
| `T2` energy  | `3334244`  | `0x0032e064` |
| `T3` energy  | `2333`     | `0x0000091d` |
| `T4` energy  | `2145623`  | `0x0020bd57` |

Command hex dump: `0f 10 02 66 f2 ae 00 32 e0 64 00 00 09 1d 00 20 bd 57`

#### A- energy with 3 tariffs:

| Field                  | Value      | Hex          |
| ---------------------- | ---------- | ------------ |
| command id             | `15`       | `0x0f`       |
| command size           | `13`       | `0x0d`       |
| energy type with flags |            | `0xd0`       |
| `T1` energy            | `40301230` | `0x0266f2ae` |
| `T2` energy            | `null`     | -            |
| `T3` energy            | `2333`     | `0x0000091d` |
| `T4` energy            | `2145623`  | `0x0020bd57` |

Command hex dump: `0f 0d d0 02 66 f2 ae 00 00 09 1d 00 20 bd 57`


## See also

* [Access level](../basics.md#command-access-level)
