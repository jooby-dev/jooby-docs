# GetExtendedCurrentValues2

Request/response to get additional current parameters.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x2d` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `45`  | `0x2d` |
| command size | `0`   | `0x00` |

Command hex dump: `2d 00`


## Response

### Format

| Size | Type     | Field                             |
| ---- | -------- | --------------------------------- |
| `1`  | `uint8`  | command id = `0x2d`               |
| `1`  | `uint8`  | command size = `7`                |
| `2`  | `uint16` | current battery voltage           |
| `1`  | `uint8`  | [relay status 1](#relay-status-1) |
| `1`  | `uint8`  | [relay status 2](#relay-status-2) |
| `1`  | `uint8`  | [status 1](#status-1)             |
| `1`  | `uint8`  | [status 2](#status-2)             |
| `1`  | `uint8`  | [status 3](#status-3)             |

### Parameters

#### relay status 1

Bit mask:

| Name                 | Bit | Description                                        |
| -------------------- | --- | -------------------------------------------------- |
| `RELAY_STATE`        | `0` | current relay state: `1` - enabled, `0` - disabled |
| `RELAY_UBAD`         | `1` | relay disabled due to poor voltage quality         |
| `RELAY_UNEQ_CURRENT` | `4` | relay disabled due to current imbalance            |
| `RELAY_OFF_CENTER`   | `5` | relay disabled from the control center             |
| `RELAY_IMAX`         | `6` | relay disabled due to maximum current              |
| `RELAY_PMAX`         | `7` | relay disabled due to maximum power                |

#### relay status 2

| Name                           | Bit | Description                                                                   |
| ------------------------------ | --- | ----------------------------------------------------------------------------- |
| `RELAY_COSFI`                  | `0` | relay disabled due to `cos φ`                                                 |
| `RELAY_SALDO_OFF_FLAG`         | `1` | relay disabled due to balance                                                 |
| `RELAY_UNEQUAL_CURRENT_OFF`    | `2` | relay disabled due to current imbalance between phase and neutral             |
| `RELAY_BIPOLAR_POWER_OFF`      | `3` | relay disabled due to opposing power directions in phase and neutral          |
| `RELAY_SALDO_OFF_ON_MAX_POWER` | `4` | relay disabled due to exceeding permissible power in balance restriction mode |
| `RELAY_HARD_ST1`               | `5` | relay enabled by hardware                                                     |

#### status 1

| Name    | Bit | Description                 |
| ------- | --- | --------------------------- |
| `MAXVA` | `0` | voltage above threshold     |
| `MINVA` | `1` | voltage below threshold     |
| `MAXT`  | `2` | temperature above threshold |
| `MINT`  | `3` | temperature below threshold |
| `MAXF`  | `4` | frequency above threshold   |
| `MINF`  | `5` | frequency below threshold   |
| `MAXIA` | `6` | current above threshold     |
| `MAXP`  | `7` | power above threshold       |

#### status 2

| Name               | Bit | Description                   |
| ------------------ | --- | ----------------------------- |
| `MAX_POWER_SALDO`  | `0` | power exceeded in credit mode |
| `BATTERY_VBAT_BAD` | `1` | low battery voltage           |
| `CLOCK_UNSET`      | `3` | clock not synchronized        |
| `MIN_COS_FI`       | `5` | `cos φ` below threshold       |

#### status 3

| Name               | Bit | Description                                     |
| ------------------ | --- | ----------------------------------------------- |
| `UNEQUAL_CURRENT`  | `0` | current imbalance                               |
| `BIPOLAR_POWER`    | `1` | opposing power directions in phases `A` and `B` |
| `POWER_A_NEGATIVE` | `6` | negative power in phase `A`                     |
| `POWER_B_NEGATIVE` | `7` | negative power in phase `B`                     |

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
            <td><code>45</code></td>
            <td><code>0x2d</code></td>
        </tr>
        <tr>
            <td>command size</td>
            <td><code>7</code></td>
            <td><code>0x07</code></td>
        </tr>
        <tr>
            <td>current battery voltage</td>
            <td><code>358</code></td>
            <td><code>0x0166</code></td>
        </tr>
        <tr>
            <td>
                <a href="#relay-status-1">relay status 1</a>
            </td>
            <td>
                <code>RELAY_STATE</code>: <code>true</code><br>
                <code>RELAY_UBAD</code>: <code>false</code><br>
                <code>RELAY_UNEQ_CURRENT</code>: <code>false</code><br>
                <code>RELAY_OFF_CENTER</code>: <code>true</code><br>
                <code>RELAY_IMAX</code>: <code>true</code><br>
                <code>RELAY_PMAX</code>: <code>false</code>
            </td>
            <td><code>0x61</code></td>
        </tr>
        <tr>
            <td>
                <a href="#relay-status-2">relay status 2</a>
            </td>
            <td>
                <code>RELAY_COSFI</code>: <code>true</code><br>
                <code>RELAY_SALDO_OFF_FLAG</code>: <code>false</code><br>
                <code>RELAY_UNEQUAL_CURRENT_OFF</code>: <code>false</code><br>
                <code>RELAY_BIPOLAR_POWER_OFF</code>: <code>false</code><br>
                <code>RELAY_SALDO_OFF_ON_MAX_POWER</code>: <code>false</code><br>
                <code>RELAY_HARD_ST1</code>: <code>true</code>
            </td>
            <td><code>0x21</code></td>
        </tr>
        <tr>
            <td>
                <a href="#status-1">status 1</a>
            </td>
            <td>
                <code>MAXVA</code>: <code>true</code><br>
                <code>MINVA</code>: <code>false</code><br>
                <code>MAXT</code>: <code>false</code><br>
                <code>MINT</code>: <code>true</code><br>
                <code>MAXF</code>: <code>true</code><br>
                <code>MINF</code>: <code>false</code><br>
                <code>MAXIA</code>: <code>true</code><br>
                <code>MAXP</code>: <code>false</code>
            </td>
            <td><code>0x59</code></td>
        </tr>
        <tr>
            <td>
                <a href="#status-2">status 2</a>
            </td>
            <td>
                <code>MAX_POWER_SALDO</code>: <code>false</code><br>
                <code>BATTERY_VBAT_BAD</code>: <code>true</code><br>
                <code>CLOCK_UNSET</code>: <code>true</code><br>
                <code>MIN_COS_FI</code>: <code>false</code>
            </td>
            <td><code>0x0a</code></td>
        </tr>
        <tr>
            <td>
                <a href="#status-3">status 3</a>
            </td>
            <td>
                <code>UNEQUAL_CURRENT</code>: <code>true</code><br>
                <code>BIPOLAR_POWER</code>: <code>false</code><br>
                <code>POWER_A_NEGATIVE</code>: <code>false</code><br>
                <code>POWER_B_NEGATIVE</code>: <code>true</code>
            </td>
            <td><code>0x81</code></td>
        </tr>
    </tbody>
</table>

Command hex dump: `2d 04 0166 61 21 59 0a 81`


## See also

* [Access level](../basics.md#command-access-level)
