# GetOpParamsExt3

Request/response to get device operator extended parameters `3`.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x71` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `113` | `0x71` |
| command size | `0`   | `0x00` |

Message hex dump: `71 00`


## Response

### Format

| Size | Type     | Field                                                              |
| ---- | -------- | ------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x71`                                                |
| `1`  | `uint8`  | command size = `17`                                                |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T1`, Watts |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T2`, Watts |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T3`, Watts |
| `4`  | `uint32` | maximum threshold for negative active power for tariff `T4`, Watts |
| `1`  | `uint8`  | [relay set](#relay-set)                                            |

### Parameters

#### Relay set

Bit mask:

| Name                         | Bit | Description                                                      |
| ---------------------------- | --- | ---------------------------------------------------------------- |
| `RELAY_OFF_LIMIT_P_MINUS_T1` | `3` | disable by exceeding negative active power limit for tariff `T1` |
| `RELAY_OFF_LIMIT_P_MINUS_T1` | `4` | disable by exceeding negative active power limit for tariff `T2` |
| `RELAY_OFF_LIMIT_P_MINUS_T1` | `5` | disable by exceeding negative active power limit for tariff `T3` |
| `RELAY_OFF_LIMIT_P_MINUS_T1` | `6` | disable by exceeding negative active power limit for tariff `T4` |

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
      <td><code>113</code></td>
      <td><code>0x71</code></td>
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

Command hex dump: `71 11 00000064 000000c8 0000012c 00000190 28`


## See also

* [Access level](../basics.md#command-access-level)
