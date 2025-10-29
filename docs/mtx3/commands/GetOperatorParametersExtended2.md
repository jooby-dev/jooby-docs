# GetOperatorParametersExtended2

Request/response to get device operator extended parameters `2`.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x47` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `71`  | `0x47` |
| command size | `0`   | `0x00` |

Message hex dump: `47 00`


## Response

### Format

| Size | Type     | Field                                                                                                                                                       |
| ---- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x47`                                                                                                                                         |
| `1`  | `uint8`  | command size = `30`                                                                                                                                         |
| `1`  | `uint8`  | allowed correction interval (`15` minutes by default)                                                                                                       |
| `1`  | `uint8`  | timeout for relay shutdown upon magnetic interference, seconds                                                                                              |
| `1`  | `uint8`  | [relay set](#relay-set)                                                                                                                                     |
| `1`  | `uint8`  | timeout for relay activation after magnetic field removal, seconds                                                                                          |
| `1`  | `uint8`  | default PLC phase<br>`0`, `1` - phase `A`<br>`2` - phase `B`<br>`3` - phase `C`                                                                             |
| `4`  | `uint32` | [display settings 1](./GetOperatorParameters.md#display-settings-1)                                                                                         |
| `4`  | `uint32` | [display settings 2](./GetOperatorParameters.md#display-settings-2)                                                                                         |
| `4`  | `uint32` | [display settings 3](./GetOperatorParameters.md#display-settings-3)                                                                                         |
| `4`  | `uint32` | [display settings 4](./GetOperatorParameters.md#display-settings-4)                                                                                         |
| `1`  | `uint8`  | [archive channel 1](#archive-channel) (if enabled, it will use half of the `A+` archive space)                                                              |
| `1`  | `uint8`  | [archive channel 2](#archive-channel) (if enabled, it will use half of the `A+R+` archive space)                                                            |
| `1`  | `uint8`  | [archive channel 3](#archive-channel) (if enabled, it will use half of the `A+R-` archive space)                                                            |
| `1`  | `uint8`  | [archive channel 4](#archive-channel) (if enabled, it will use half of the `A-` archive space)                                                              |
| `1`  | `uint8`  | [archive channel 5](#archive-channel) (if enabled, it will use half of the `A-R+` archive space)                                                            |
| `1`  | `uint8`  | [archive channel 6](#archive-channel) (if enabled, it will use half of the `A-R-` archive space)                                                            |
| `1`  | `uint8`  | allowed correction period, hours (`24` hours by default). If bit `7` is `0` (default is `0`), time correction crossing the half-hour boundary is forbidden. |

### Parameters

#### relay set

Bit mask:

| Name                      | Bit | Description                                            |
| ------------------------- | --- | ------------------------------------------------------ |
| `RELAY_OFF_MAGNET`        | `0` | disable relay upon detection of magnetic field         |
| `RELAY_ON_MAGNET_TIMEOUT` | `1` | enable relay after `timeoutRelayOn` timeout (not used) |
| `RELAY_ON_MAGNET_AUTO`    | `2` | enable relay after removal of magnetic field           |

#### archive channel

| Value | Archive type                                 |
| ----- | -------------------------------------------- |
| `0`   | Do not archive                               |
| `1`   | `1/3/5/10/15/30/60`-minute `A+` phase `A`    |
| `2`   | `1/3/5/10/15/30/60`-minute `A+` phase `B`    |
| `3`   | `1/3/5/10/15/30/60`-minute `A+` phase `C`    |
| `4`   | `1/3/5/10/15/30/60`-minute `A-` phase `A`    |
| `5`   | `1/3/5/10/15/30/60`-minute `A-` phase `B`    |
| `6`   | `1/3/5/10/15/30/60`-minute `A-` phase `C`    |
| `7`   | `1/3/5/10/15/30/60`-minute `A+R+` phase `A`  |
| `8`   | `1/3/5/10/15/30/60`-minute `A+R+` phase `B`  |
| `9`   | `1/3/5/10/15/30/60`-minute `A+R+` phase `C`  |
| `10`  | `1/3/5/10/15/30/60`-minute `A+R-` phase `A`  |
| `11`  | `1/3/5/10/15/30/60`-minute `A+R-` phase `B`  |
| `12`  | `1/3/5/10/15/30/60`-minute `A+R-` phase `C`  |
| `13`  | `1/3/5/10/15/30/60`-minute `A-R+` phase `A`  |
| `14`  | `1/3/5/10/15/30/60`-minute `A-R+` phase `B`  |
| `15`  | `1/3/5/10/15/30/60`-minute `A-R+` phase `C`  |
| `16`  | `1/3/5/10/15/30/60`-minute `A-R-` phase `A`  |
| `17`  | `1/3/5/10/15/30/60`-minute `A-R-` phase `B`  |
| `18`  | `1/3/5/10/15/30/60`-minute `A-R-` phase `C`  |
| `19`  | `1/3/5/10/15/30/60`-minute `R+` phase `A`    |
| `20`  | `1/3/5/10/15/30/60`-minute `R+` phase `B`    |
| `21`  | `1/3/5/10/15/30/60`-minute `R+` phase `C`    |
| `22`  | `1/3/5/10/15/30/60`-minute `R-` phase `A`    |
| `23`  | `1/3/5/10/15/30/60`-minute `R-` phase `B`    |
| `24`  | `1/3/5/10/15/30/60`-minute `R-` phase `C`    |
| `25`  | `1/3/5/10/15/30/60`-minute voltage phase `A` |
| `26`  | `1/3/5/10/15/30/60`-minute voltage phase `B` |
| `27`  | `1/3/5/10/15/30/60`-minute voltage phase `C` |
| `28`  | `10`-minute voltage phase `A`                |
| `29`  | `10`-minute voltage phase `B`                |
| `30`  | `10`-minute voltage phase `C`                |
| `31`  | `1/3/5/10/15/30/60`-minute current phase `A` |
| `32`  | `1/3/5/10/15/30/60`-minute current phase `B` |
| `33`  | `1/3/5/10/15/30/60`-minute current phase `C` |

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
            <td><code>71</code></td>
            <td><code>0x47</code></td>
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
            <td>
                <code>RELAY_OFF_MAGNET</code>: <code>true</code><br>
                <code>RELAY_ON_MAGNET_TIMEOUT</code>: <code>false</code><br>
                <code>RELAY_ON_MAGNET_AUTO</code>: <code>true</code>
            </td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>timeout for relay activation after magnetic field removal, seconds</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>default PLC phase</td>
            <td><code>1</code></td>
            <td><code>0x01</code></td>
        </tr>
        <tr>
            <td><a href="#display-settings-1">display settings 1</a></td>
            <td>
                <code>SET_ALL_SEGMENT_DISPLAY</code>: <code>false</code><br>
                <code>SOFTWARE_VERSION</code>: <code>false</code><br>
                <code>TOTAL_ACTIVE_ENERGY</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_REACTIVE_ENERGY</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_NEGATIVE_REACTIVE_ENERGY</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>NEGATIVE_REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_EXPORTED_ACTIVE_ENERGY</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>EXPORTED_ACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_EXPORTED_REACTIVE_ENERGY</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>EXPORTED_REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_EXPORTED_NEGATIVE_REACTIVE_ENERGY</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>EXPORTED_NEGATIVE_REACTIVE_ENERGY_T4</code>: <code>false</code>
            </td>
            <td><code>0x00000000</code></td>
        </tr>
        <tr>
            <td><a href="#display-settings-2">display settings 2</a></td>
            <td>
                <code>CURRENT_IN_PHASE_A</code>: <code>false</code><br>
                <code>CURRENT_IN_PHASE_B</code>: <code>false</code><br>
                <code>CURRENT_IN_PHASE_C</code>: <code>false</code><br>
                <code>CURRENT_IN_NEUTRAL</code>: <code>false</code><br>
                <code>VOLTAGE_IN_PHASE_A</code>: <code>false</code><br>
                <code>VOLTAGE_IN_PHASE_B</code>: <code>false</code><br>
                <code>VOLTAGE_IN_PHASE_C</code>: <code>false</code><br>
                <code>BATTERY_VOLTAGE</code>: <code>false</code><br>
                <code>FREQUENCY</code>: <code>false</code><br>
                <code>ACTIVE_POWER_SUM</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_A</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_B</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_C</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_SUM</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_A</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_B</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_C</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_SUM</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_PHASE_A</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_PHASE_B</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_PHASE_C</code>: <code>false</code><br>
                <code>TOTAL_POWER_FACTOR</code>: <code>false</code><br>
                <code>POWER_FACTOR_PHASE_A</code>: <code>false</code><br>
                <code>POWER_FACTOR_PHASE_B</code>: <code>false</code><br>
                <code>POWER_FACTOR_PHASE_C</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_SUM</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_PHASE_A</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_PHASE_B</code>: <code>false</code><br>
                <code>APPARENT_POWER_QPLUS_PHASE_C</code>: <code>false</code><br>
                <code>APPARENT_POWER_QMINUS_SUM</code>: <code>false</code><br>
                <code>APPARENT_POWER_QMINUS_PHASE_A</code>: <code>false</code><br>
                <code>APPARENT_POWER_QMINUS_PHASE_B</code>: <code>false</code>
            </td>
            <td><code>0x00000000</code></td>
        </tr>
        <tr>
            <td><a href="#display-settings-3">display settings 3</a></td>
            <td>
                <code>APPARENT_POWER_QMINUS_PHASE_C</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_ACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T3</code>: <code>false</code>
            </td>
            <td><code>0x00000000</code></td>
        </tr>
        <tr>
            <td><a href="#display-settings-4">display settings 4</a></td>
            <td>
                <code>MAX_EXPORTED_ACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_EXPORTED_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_DAY_T4</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T1</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T2</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T3</code>: <code>false</code><br>
                <code>MAX_NEGATIVE_EXPORTED_REACTIVE_POWER_MONTH_T4</code>: <code>false</code><br>
                <code>HOUR_MINUTE_SECOND</code>: <code>false</code><br>
                <code>DATE_MONTH_YEAR</code>: <code>false</code><br>
                <code>CURRENT_TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>VOLTAGE_TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>CURRENT_BALANCE</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T1</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T2</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T3</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T4</code>: <code>false</code><br>
                <code>OPTOPORT_SPEED</code>: <code>true</code><br>
                <code>MAGNET_INDUCTION</code>: <code>false</code>
            </td>
            <td><code>0x40000000</code></td>
        </tr>
        <tr>
            <td><a href="#archive-channel">archive channel 1</a></td>
            <td><code>1</code></td>
            <td><code>0x01</code></td>
        </tr>
        <tr>
            <td><a href="#archive-channel">archive channel 2</a></td>
            <td><code>2</code></td>
            <td><code>0x02</code></td>
        </tr>
        <tr>
            <td><a href="#archive-channel">archive channel 3</a></td>
            <td><code>3</code></td>
            <td><code>0x03</code></td>
        </tr>
        <tr>
            <td><a href="#archive-channel">archive channel 4</a></td>
            <td><code>4</code></td>
            <td><code>0x04</code></td>
        </tr>
        <tr>
            <td><a href="#archive-channel">archive channel 5</a></td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td><a href="#archive-channel">archive channel 6</a></td>
            <td><code>6</code></td>
            <td><code>0x06</code></td>
        </tr>
        <tr>
            <td>allowed correction period, hours</td>
            <td><code>152</code></td>
            <td><code>0x98</code></td>
        </tr>
    </tbody>
</table>

Command hex dump: `47 1c 0f 05 05 05 01 00000000 00000000 00000000 04000000 01 02 03 04 05 06 98`


## See also

* [Access level](../basics.md#command-access-level)
