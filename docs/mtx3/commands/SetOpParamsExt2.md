# SetOpParamsExt2

Request/response to set device operator parameters `2`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                                                                                                       |
| ---- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x45`                                                                                                                                         |
| `1`  | `uint8`  | command size = `28`                                                                                                                                         |
| `1`  | `uint8`  | allowed correction interval (`15` minutes by default)                                                                                                       |
| `1`  | `uint8`  | timeout for relay shutdown upon magnetic interference, seconds                                                                                              |
| `1`  | `uint8`  | [relay set](#relay-set)                                                                                                                                     |
| `1`  | `uint8`  | timeout for relay activation after magnetic field removal, seconds                                                                                          |
| `1`  | `uint8`  | default PLC Phase<br>`0`, `1` - Phase A<br>`2` - Phase B<br>`3` - Phase C                                                                                   |
| `4`  | `uint32` | [display settings 1](./GetOpParams.md#display-settings-1)                                                                                                   |
| `4`  | `uint32` | [display settings 2](./GetOpParams.md#display-settings-2)                                                                                                   |
| `4`  | `uint32` | [display settings 3](./GetOpParams.md#display-settings-3)                                                                                                   |
| `4`  | `uint32` | [display settings 4](./GetOpParams.md#display-settings-4)                                                                                                   |
| `1`  | `uint8`  | [channel load profile 1](./GetOpParamsExt2.md#channel-load-profile) (if enabled, it will use half of the `A+` archive space)                                |
| `1`  | `uint8`  | [channel load profile 2](./GetOpParamsExt2.md#channel-load-profile) (if enabled, it will use half of the `A+R+` archive space                               |
| `1`  | `uint8`  | [channel load profile 3](./GetOpParamsExt2.md#channel-load-profile) (if enabled, it will use half of the `A+R-` archive space)                              |
| `1`  | `uint8`  | [channel load profile 4](./GetOpParamsExt2.md#channel-load-profile) (if enabled, it will use half of the `A-` archive space)                                |
| `1`  | `uint8`  | [channel load profile 5](./GetOpParamsExt2.md#channel-load-profile) (if enabled, it will use half of the `A-R+` archive space)                              |
| `1`  | `uint8`  | [channel load profile 6](./GetOpParamsExt2.md#channel-load-profile) (if enabled, it will use half of the `A-R-` archive space)                              |
| `1`  | `uint8`  | allowed correction period, hours (`24` hours by default). If bit `7` is `0` (default is `0`), time correction crossing the half-hour boundary is forbidden. |


### Examples

<table>
  <thead>
    <tr>
      <th>Field</th>
      <th>Value</th>
      <th>Hex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>command id</td>
      <td><code>69</code></td>
      <td><code>0x45</code></td>
    </tr>
    <tr>
      <td>command size</td>
      <td><code>28</code></td>
      <td><code>0x1c</code></td>
    </tr>
    <tr>
      <td>allowed correction interval (<code>15</code> minutes by default)</td>
      <td><code>15</code></td>
      <td><code>0x0f</code></td>
    </tr>
    <tr>
      <td>timeout for relay shutdown upon magnetic interference, seconds</td>
      <td><code>5</code></td>
      <td><code>0x05</code></td>
    </tr>
    <tr>
      <td><a href="#relay-set">relay set</a></td>
      <td><code>5</code></td>
      <td><code>0x05</code></td>
    </tr>
    <tr>
      <td>timeout for relay activation after magnetic field removal, seconds</td>
      <td><code>5</code></td>
      <td><code>0x05</code></td>
    </tr>
    <tr>
      <td>default PLC Phase</td>
      <td><code>1</code></td>
      <td><code>0x01</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-1">display settings 1</a></td>
      <td><code>?</code></td>
      <td><code>0x00000000</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-2">display settings 2</a></td>
      <td><code>?</code></td>
      <td><code>0x00000000</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-3">display settings 3</a></td>
      <td><code>?</code></td>
      <td><code>0x00000000</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-4">display settings 4</a></td>
      <td><code>?</code></td>
      <td><code>0x40000000</code></td>
    </tr>
    <tr>
      <td><a href="#channel-load-profile">channel load profile 1</a></td>
      <td><code>1</code></td>
      <td><code>0x01</code></td>
    </tr>
    <tr>
      <td><a href="#channel-load-profile">channel load profile 2</a></td>
      <td><code>2</code></td>
      <td><code>0x02</code></td>
    </tr>
    <tr>
      <td><a href="#channel-load-profile">channel load profile 3</a></td>
      <td><code>3</code></td>
      <td><code>0x03</code></td>
    </tr>
    <tr>
      <td><a href="#channel-load-profile">channel load profile 4</a></td>
      <td><code>4</code></td>
      <td><code>0x04</code></td>
    </tr>
    <tr>
      <td><a href="#channel-load-profile">channel load profile 5</a></td>
      <td><code>5</code></td>
      <td><code>0x05</code></td>
    </tr>
    <tr>
      <td><a href="#channel-load-profile">channel load profile 6</a></td>
      <td><code>6</code></td>
      <td><code>0x06</code></td>
    </tr>
    <tr>
      <td>allowed correction period, hours</td>
      <td><code>?</code></td>
      <td><code>0x98</code></td>
    </tr>
  </tbody>
</table>

Command hex dump: `47 1c 0f 05 05 05 01 00000000 00000000 00000000 04000000 01 02 03 04 05 06 98`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x45` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `69`  | `0x45` |
| command size | `0`   | `0x00` |

Command hex dump: `45 00`


## See also

* [Access level](../basics.md#command-access-level)
