# SetOperatorParametersExtended

Request/response to set device operator parameters.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                                                                                  |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x3f`                                                                                                    |
| `1`  | `uint8` | command size = `9`                                                                                                     |
| `1`  | `uint8` | timeout for automatic relay activation based on `IMAX`, `PMAX`, `IDIFF`, `COSFI`, minutes                              |
| `1`  | `uint8` | [define 1](./GetOperatorParametersExtended.md#define-1)                                                                |
| `1`  | `uint8` | timeout for relay reactivation by button after deactivation due to `IMAX`, `PMAX`, `IDIFF`, or `COSFI` limits, seconds |
| `1`  | `uint8` | timeout for relay activation upon restoration of quality voltage, seconds                                              |
| `5`  | `uint8` | reserved bytes                                                                                                         |

### Examples

<table>
    <tr>
        <th>Field</th>
        <th>Value</th>
        <th>Hex</th>
    </tr>
    <tr>
        <td>command id</td>
        <td><code>64</code></td>
        <td><code>0x40</code></td>
    </tr>
    <tr>
        <td>command size</td>
        <td><code>9</code></td>
        <td><code>0x9</code></td>
    </tr>
    <tr>
        <td>timeout for automatic relay activation based on <code>IMAX</code>, <code>PMAX</code>, <code>IDIFF</code>, <code>COSFI</code>, minutes</td>
        <td><code>1</code></td>
        <td><code>0x01</code></td>
    </tr>
    <tr>
        <td>
            <a href="./GetOperatorParameters.md#define-1">define 1</a>
        </td>
        <td>
            <code>RESET_DAY_MAX_POWER_KEY</code>: <code>false</code><br>
            <code>RESET_MONTH_MAX_POWER_KEY</code>: <code>false</code><br>
            <code>BLOCK_KEY_OPTOPORT</code>: <code>false</code><br>
            <code>MAGNET_SCREEN_CONST</code>: <code>false</code><br>
        </td>
        <td><code>0x00</code></td>
    </tr>
    <tr>
        <td>timeout for relay reactivation by button after deactivation due to <code>IMAX</code>, <code>PMAX</code>, <code>IDIFF</code>, or <code>COSFI</code> limits, seconds</td>
        <td><code>0</code></td>
        <td><code>0x00</code></td>
    </tr>
    <tr>
        <td>timeout for relay activation upon restoration of quality voltage, seconds</td>
        <td><code>5</code></td>
        <td><code>0x05</code></td>
    </tr>
    <tr>
        <td>reserved bytes</td>
        <td><code>0</code></td>
        <td><code>0x0000000000</code></td>
    </tr>
</table>

Command hex dump: `40 09 01 00 00 05 0000000000`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x40` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `31`  | `0x40` |
| command size | `0`   | `0x00` |

Command hex dump: `40 00`


## See also

* [Access level](../basics.md#command-access-level)
