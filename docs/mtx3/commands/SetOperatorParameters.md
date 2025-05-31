# SetOperatorParameters

Request/response to set device operator parameters.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                                                                                                               |
| ---- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x1f`                                                                                                                                                 |
| `1`  | `uint8`  | command size = `95`                                                                                                                                                 |
| `4`  | `uint32` | maximum voltage threshold, mV                                                                                                                                       |
| `4`  | `uint32` | minimum voltage threshold, mV                                                                                                                                       |
| `4`  | `uint32` | maximum current threshold, mA                                                                                                                                       |
| `4`  | `uint32` | maximum active power threshold for tariff `T1`, Watts                                                                                                               |
| `4`  | `uint32` | maximum active power threshold for tariff `T2`, Watts                                                                                                               |
| `4`  | `uint32` | maximum active power threshold for tariff `T3`, Watts                                                                                                               |
| `4`  | `uint32` | maximum active power threshold for tariff `T4`, Watts                                                                                                               |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T1`, volt-ampere reactive                                                                                              |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T2`, volt-ampere reactive                                                                                              |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T3`, volt-ampere reactive                                                                                              |
| `4`  | `uint32` | maximum reactive power threshold for tariff `T4`, volt-ampere reactive                                                                                              |
| `1`  | `uint8`  | power averaging interval, in minutes                                                                                                                                |
| `1`  | `uint8`  | start date of the monthly billing period                                                                                                                            |
| `1`  | `uint8`  | display active time                                                                                                                                                 |
| `1`  | `uint8`  | display active time for each screen                                                                                                                                 |
| `4`  | `uint32` | [display settings 1](./GetOperatorParameters.md#display-settings-1)                                                                                                 |
| `4`  | `uint32` | [display settings 2](./GetOperatorParameters.md#display-settings-2)                                                                                                 |
| `4`  | `uint32` | [display settings 3](./GetOperatorParameters.md#display-settings-3)                                                                                                 |
| `4`  | `uint32` | [relay set](./GetOperatorParameters.md#relay-set)                                                                                                                   |
| `1`  | `uint8`  | [serial ports set](./GetOperatorParameters.md#serial-ports-set)                                                                                                     |
| `1`  | `uint8`  | integration period for energy profiles `A+`, `A-`, voltage VA , `0`, `30` - `30`, `1`, `3`, `5`, `10`, `15`, `60` minutes (`ten`)                                   |
| `1`  | `uint8`  | voltage averaging interval `0`, `1`, `3`, `5`, `10`, `15`, `30`, `60` minutes to detect voltage quality                                                             |
| `1`  | `uint8`  | reserved byte                                                                                                                                                       |
| `1`  | `uint8`  | interval for tracking power off events, in minutes                                                                                                                  |
| `1`  | `uint8`  | reserved byte                                                                                                                                                       |
| `1`  | `uint8`  | timeout for relay deactivation due to poor voltage, seconds                                                                                                         |
| `1`  | `unt8`   | maximum threshold for the frequency of the grid voltage                                                                                                             |
| `1`  | `unt8`   | minimum threshold for the frequency of the grid voltage                                                                                                             |
| `1`  | `uint8`  | year of parameters recording                                                                                                                                        |
| `1`  | `uint8`  | month of parameters recording                                                                                                                                       |
| `1`  | `uint8`  | date of parameters recording                                                                                                                                        |
| `1`  | `uint8`  | the number of digits after the decimal point for displaying energy values<br>`0x00` - no digits<br>`0x01` - `1` digit<br>`0x02` - `2` digits<br>`0x03` - `3` digits |
| `2`  | `int16`  | numerator of the current transformation ratio                                                                                                                       |
| `2`  | `int16`  | denominator of the current transformation ratio                                                                                                                     |
| `2`  | `int16`  | numerator of the voltage transformation ratio                                                                                                                       |
| `2`  | `int16`  | denominator of the voltage transformation ratio                                                                                                                     |
| `1`  | `uint8`  | [measurement type](./GetOperatorParameters.md#measurement-type)                                                                                                     |
| `2`  | `uint16` | minimum threshold for the `cos φ` value                                                                                                                             |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum current                                                                                                             |
| `1`  | `uint8`  | timeout for relay deactivation based on maximum power                                                                                                               |
| `1`  | `uint8`  | timeout for relay deactivation based on `cos φ`                                                                                                                     |
| `1`  | `uint8`  | `PMAX` settings<br>`0` - `PMAX` = `POWER_A` + `POWER_B` + `POWER_C`<br>`1` - `PMAX` averaged power over the integration period                                      |
| `4`  | `uint32` | [display settings 4](./GetOperatorParameters.md#display-settings-4)                                                                                                 |

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
            <td><code>31</code></td>
            <td><code>0x1f</code></td>
        </tr>
        <tr>
            <td>command size</td>
            <td><code>95</code></td>
            <td><code>0x5f</code></td>
        </tr>
        <tr>
            <td>maximum voltage threshold, mV</td>
            <td><code>265000</code></td>
            <td><code>0x00040b28</code></td>
        </tr>
        <tr>
            <td>minimum voltage threshold, mV</td>
            <td><code>156000</code></td>
            <td><code>0x00026160</code></td>
        </tr>
        <tr>
            <td>maximum current threshold, mA</td>
            <td><code>120000</code></td>
            <td><code>0x0001d4c0</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T1</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T2</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T3</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum active power threshold for tariff <code>T4</code>, Watts</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T1</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T2</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T3</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>maximum reactive power threshold for tariff <code>T4</code>, volt-ampere reactive</td>
            <td><code>31800</code></td>
            <td><code>0x00007c38</code></td>
        </tr>
        <tr>
            <td>power averaging interval, in minutes</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>start date of the monthly billing period</td>
            <td><code>1</code></td>
            <td><code>0x01</code></td>
        </tr>
        <tr>
            <td>display active time</td>
            <td><code>127</code></td>
            <td><code>0x7f</code></td>
        </tr>
        <tr>
            <td>display active time for each screen</td>
            <td><code>7</code></td>
            <td><code>0x07</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#display-settings-1">display settings 1</a>
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
                <a href="./GetOperatorParameters.md#display-settings-2">display settings 2</a>
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
                <a href="./GetOperatorParameters.md#display-settings-3">display settings 3</a>
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
                <a href="./GetOperatorParameters.md#relay-set">relay set</a>
            </td>
            <td>
                <code>RELAY_ON_Y</code>: <code>true</code><br>
                <code>RELAY_ON_CENTER</code>: <code>true</code><br>
                <code>RELAY_ON_PB</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_ON_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_ON_V_GOOD</code>: <code>false</code><br>
                <code>RELAY_OFF_Y</code>: <code>true</code><br>
                <code>RELAY_OFF_CENTER</code>: <code>true</code><br>
                <code>RELAY_OFF_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_OFF_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_OFF_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_OFF_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_OFF_I_LIMIT</code>: <code>false</code><br>
                <code>RELAY_OFF_V_BAD</code>: <code>false</code><br>
                <code>RELAY_OFF_DIFF_BAD</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_1</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_2</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_3</code>: <code>false</code><br>
                <code>RELAY_OFF_LIM_VAR_TARIFF_4</code>: <code>false</code><br>
                <code>RELAY_ON_PF_MIN</code>: <code>false</code><br>
                <code>RELAY_OFF_PF_MIN</code>: <code>false</code><br>
                <code>RELAY_ON_TIMEOUT</code>: <code>false</code><br>
                <code>RELAY_ON_SALDO</code>: <code>false</code><br>
                <code>RELAY_OFF_SALDO</code>: <code>false</code><br>
                <code>RELAY_OFF_SALDO_SOFT</code>: <code>false</code>
            </td>
            <td><code>0x00000303</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#serial-ports-set">serial-ports-set</a>
            </td>
            <td>
                <code>plc</code>: <code>9600</code><br>
                <code>optoport</code>: <code>9600</code>
            </td>
            <td><code>0x44</code></td>
        </tr>
        <tr>
            <td>integration period for energy profiles <code>A+</code>, <code>A-</code>, voltage</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>voltage averaging interval to detect voltage quality</td>
            <td><code>30</code></td>
            <td><code>0x1e</code></td>
        </tr>
        <tr>
            <td>interval for tracking power off events, in minutes</td>
            <td><code>3</code></td>
            <td><code>0x03</code></td>
        </tr>
        <tr>
            <td>reserved byte</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation due to poor voltage, seconds</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>maximum threshold for the frequency of the grid voltage</td>
            <td><code>55</code></td>
            <td><code>0x37</code></td>
        </tr>
        <tr>
            <td>minimum threshold for the frequency of the grid voltage</td>
            <td><code>45</code></td>
            <td><code>0x2d</code></td>
        </tr>
        <tr>
            <td>year of parameters recording</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>month of parameters recording</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>date of parameters recording</td>
            <td><code>0</code></td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>the number of digits after the decimal point for displaying energy values</td>
            <td><code>2</code></td>
            <td><code>0x02</code></td>
        </tr>
        <tr>
            <td>numerator of the current transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>denominator of the current transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>numerator of the voltage transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>denominator of the voltage transformation ratio</td>
            <td><code>1</code></td>
            <td><code>0x0001</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#measurement-type">measurement type</a>
            </td>
            <td>
                <code>TRANSFORMATION_RATIO</code>: <code>false</code><br>
                <code>METER_TYPE_R</code>: <code>false</code><br>
                <code>ACCUMULATE_BY_R_PLUS_MINUS</code>: <code>false</code>
            </td>
            <td><code>0x00</code></td>
        </tr>
        <tr>
            <td>minimum threshold for the <code>cos φ</code> value</td>
            <td><code>0</code></td>
            <td><code>0x0000</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation based on maximum current</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation based on maximum power</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>timeout for relay deactivation based on <code>cos φ</code></td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td><code>PMAX</code> settings</td>
            <td><code>5</code></td>
            <td><code>0x05</code></td>
        </tr>
        <tr>
            <td>
                <a href="./GetOperatorParameters.md#display-settings-4">display settings 4</a>
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
    </tbody>
</table>

Command hex dump: `1f 5f 00040b28 00026160 0001d4c0 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 00007c38 1e 01 7f 07 00001085 00022200 00000000 00000303 44 1e 1e 03 00 05 37 2d 00 00 00 02 0001 0001 0001 0001 00 0000 05 05 05 01 80060000`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x1f` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `31`  | `0x1f` |
| command size | `0`   | `0x00` |

Command hex dump: `1f 00`


## See also

* [Access level](../basics.md#command-access-level)
