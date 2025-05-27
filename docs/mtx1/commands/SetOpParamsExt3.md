# SetOpParamsExt3

Request/response to set device operator parameters `3`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                              |
| ---- | -------- | ------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x72`                                                |
| `1`  | `uint8`  | command size = `17`                                                |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T1`, Watts |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T2`, Watts |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T3`, Watts |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T4`, Watts |
| `1`  | `uint8`  | [relay set](./GetOpParamsExt3.md#relay-set)                        |

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
      <td><code>114</code></td>
      <td><code>0x72</code></td>
    </tr>
    <tr>
      <td>command size</td>
      <td><code>17</code></td>
      <td><code>0x11</code></td>
    </tr>
    <tr>
      <td>relay set</td>
      <td>
        <code>RELAY_OFF_LIMIT_P_MINUS_T1</code>: <code>true</code><br>
        <code>RELAY_OFF_LIMIT_P_MINUS_T2</code>: <code>false</code><br>
        <code>RELAY_OFF_LIMIT_P_MINUS_T3</code>: <code>true</code><br>
        <code>RELAY_OFF_LIMIT_P_MINUS_T4</code>: <code>false</code>
      </td>
      <td><code>0x14</code></td>
    </tr>
  </tbody>
</table>

Command hex dump: `72 11 00000064 000000c8 0000012c 00000190 14`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x72` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `114` | `0x72` |
| command size | `0`   | `0x00` |

Command hex dump: `72 00`


## See also

* [Access level](../basics.md#command-access-level)
