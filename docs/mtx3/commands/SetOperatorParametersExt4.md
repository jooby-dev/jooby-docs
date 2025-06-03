# SetOperatorParametersExt4

Request/response to set device operator parameters `4`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                              |
| ---- | -------- | ---------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x74`                                                                |
| `1`  | `uint8`  | command size = `28`                                                                |
| `4`  | `uint32` | [main mode display settings](./GetOperatorParametersExt4.md#display-settings)      |
| `4`  | `uint32` | [extended mode display settings](./GetOperatorParametersExt4.md#display-settings)  |
| `4`  | `uint32` | [battery mode display settings 1](./GetOperatorParameters.md#display-settings-1)   |
| `4`  | `uint32` | [battery mode display settings 2](./GetOperatorParameters.md#display-settings-2)   |
| `4`  | `uint32` | [battery mode display settings 3](./GetOperatorParameters.md#display-settings-3)   |
| `4`  | `uint32` | [battery mode display settings 4](./GetOperatorParameters.md#display-settings-4)   |
| `4`  | `uint32` | [battery mode display settings 5](./GetOperatorParametersExt4.md#display-settings) |

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
            <td><code>116</code></td>
            <td><code>0x74</code></td>
        </tr>
        <tr>
            <td>command size</td>
            <td><code>28</code></td>
            <td><code>0x1c</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParametersExt4.md#display-settings">main mode display settings</a>
            </td>
            <td>
                <code>EVENT</code>: <code>true</code><br>
                <code>PROFILE_P01</code>: <code>true</code><br>
                <code>PROFILE_P02</code>: <code>false</code><br>
                <code>PROFILE_P03</code>: <code>true</code><br>
                <code>PROFILE_P04</code>: <code>true</code><br>
                <code>PROFILE_P05</code>: <code>false</code><br>
                <code>PROFILE_P06</code>: <code>true</code>
            </td>
            <td><code>0x0000005b</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParametersExt4.md#display-settings">extended mode display settings</a>
            </td>
            <td>
                <code>EVENT</code>: <code>true</code><br>
                <code>PROFILE_P01</code>: <code>false</code><br>
                <code>PROFILE_P02</code>: <code>true</code><br>
                <code>PROFILE_P03</code>: <code>false</code><br>
                <code>PROFILE_P04</code>: <code>true</code><br>
                <code>PROFILE_P05</code>: <code>false</code><br>
                <code>PROFILE_P06</code>: <code>true</code>
            </td>
            <td><code>0x00000055</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#display-settings-1">battery mode display settings 1</a>
            </td>
            <td>
                <code>SET_ALL_SEGMENT_DISPLAY</code>: <code>true</code><br>
                <code>SOFTWARE_VERSION</code>: <code>false</code><br>
                <code>TOTAL_ACTIVE_ENERGY</code>: <code>true</code><br>
                <code>ACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>ACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_REACTIVE_ENERGY</code>: <code>true</code><br>
                <code>REACTIVE_ENERGY_T1</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T2</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T3</code>: <code>false</code><br>
                <code>REACTIVE_ENERGY_T4</code>: <code>false</code><br>
                <code>TOTAL_NEGATIVE_REACTIVE_ENERGY</code>: <code>true</code><br>
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
            <td><code>0x00001085</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#display-settings-2">battery mode display settings 2</a>
            </td>
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
                <code>ACTIVE_POWER_SUM</code>: <code>true</code><br>
                <code>ACTIVE_POWER_PHASE_A</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_B</code>: <code>false</code><br>
                <code>ACTIVE_POWER_PHASE_C</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_SUM</code>: <code>true</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_A</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_B</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QPLUS_PHASE_C</code>: <code>false</code><br>
                <code>REACTIVE_POWER_QMINUS_SUM</code>: <code>true</code><br>
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
            <td><code>0x00022200</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#display-settings-3">battery mode display settings 3</a>
            </td>
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
            <td>
                <a href="./GetOperatorParameters.md#display-settings-4">battery mode display settings 4</a>
            </td>
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
                <code>HOUR_MINUTE_SECOND</code>: <code>true</code><br>
                <code>DATE_MONTH_YEAR</code>: <code>true</code><br>
                <code>CURRENT_TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>VOLTAGE_TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>CURRENT_BALANCE</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T1</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T2</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T3</code>: <code>false</code><br>
                <code>POWER_THRESHOLD_T4</code>: <code>false</code><br>
                <code>SORT_DISPLAY_SCREENS</code>: <code>false</code><br>
                <code>AUTO_SCREEN_SCROLLING</code>: <code>true</code>
            </td>
            <td><code>0x80060000</code></td>
        </tr>
        <tr>
            <td><a href="./GetOperatorParametersExt4.md#display-settings">battery mode display settings 5</a></td>
            <td>
                <code>EVENT</code>: <code>false</code><br>
                <code>PROFILE_P01</code>: <code>false</code><br>
                <code>PROFILE_P02</code>: <code>true</code><br>
                <code>PROFILE_P03</code>: <code>true</code><br>
                <code>PROFILE_P04</code>: <code>true</code><br>
                <code>PROFILE_P05</code>: <code>false</code><br>
                <code>PROFILE_P06</code>: <code>false</code>
            </td>
            <td><code>0x0000001c</code></td>
        </tr>
    </tbody>
</table>

Command hex dump: `74 1c 0000005b 00000055 00001085 00022200 00000000 80060000 0000001c`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x74` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `116` | `0x74` |
| command size | `0`   | `0x00` |

Command hex dump: `75 00`


## See also

* [Access level](../basics.md#command-access-level)
