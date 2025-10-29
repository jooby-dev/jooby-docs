# GetCurrentStatusMeter

Request/response to get the current status from device.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x39` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `57`  | `0x39` |
| command size | `0`   | `0x00` |

Command hex dump: `39 00`


## Response

### Format

| Size | Type     | Field                                                                                    |
| ---- | -------- | ---------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x39`                                                                      |
| `1`  | `uint8`  | command size = `31`                                                                      |
| `4`  | `uint32` | total operating time since first power-on, seconds                                       |
| `4`  | `uint32` | duration of poor voltage during the accounting period, seconds                           |
| `4`  | `uint32` | duration of maximum current during the accounting period, seconds                        |
| `4`  | `uint32` | duration of maximum power during the accounting period, seconds                          |
| `4`  | `uint32` | reserved                                                                                 |
| `4`  | `uint32` | duration of frequency deviation from normal during the accounting period, seconds        |
| `1`  | `uint8`  | [relay status](#relay-status)                                                            |
| `1`  | `uint8`  | [event status](./GetEventStatus.md#status-event-set-1)                                   |
| `1`  | `uint8`  | [event status2](./GetEventStatus.md#status-event-set-2)                                  |
| `1`  | `uint8`  | [calibration flags](#calibration-flags)                                                  |
| `1`  | `uint8`  | current tariff `A+`                                                                      |
| `1`  | `uint8`  | current tariff `A-`                                                                      |
| `1`  | `uint8`  | current daylight saving time status (summer/winter time)<br>`0` - winter<br>`1` - summer |

### Parameters

#### relay status

Bit mask:

| Name                 | Bit | Description                                  |
| -------------------- | --- | -------------------------------------------- |
| `RELAY_STATE`        | `0` | current relay state<br>`0` - off<br>`1` - on |
| `RELAY_UBAD`         | `1` | relay turned off due to poor voltage         |
| `RELAY_UNEQ_CURRENT` | `4` | relay switched off due to unequal currents   |
| `RELAY_OFF_CENTER`   | `5` | relay switched off from the control center   |
| `RELAY_IMAX`         | `6` | relay turned off due to overcurrent          |
| `RELAY_PMAX`         | `7` | relay turned off due to overpower            |

#### calibration flags

Bit mask:

| Name          | Bit | Description      |
| ------------- | --- | ---------------- |
| `CALIBRATION` | `0` | calibration mode |
| `HARD_KEY`    | `1` | hard key mode    |

### Examples

<table>
    <tr>
        <th>Field</th>
        <th>Value</th>
        <th>Hex</th>
    </tr>
    <tr>
        <td>command id</td>
        <td><code>57</code></td>
        <td><code>0x39</code></td>
    </tr>
    <tr>
        <td>command size</td>
        <td><code>31</code></td>
        <td><code>0x1f</code></td>
    </tr>
    <tr>
        <td>total operating time, seconds</td>
        <td><code>16781313</code></td>
        <td><code>0x01001001</code></td>
    </tr>
    <tr>
        <td>duration of poor voltage during the accounting period, seconds</td>
        <td><code>120</code></td>
        <td><code>0x00000078</code></td>
    </tr>
    <tr>
        <td>duration of maximum current during the accounting period, seconds</td>
        <td><code>121</code></td>
        <td><code>0x00000079</code></td>
    </tr>
    <tr>
        <td>duration of maximum power during the accounting period, seconds</td>
        <td><code>30</code></td>
        <td><code>0x0000001e</code></td>
    </tr>
    <tr>
        <td>reserved</td>
        <td><code>0</code></td>
        <td><code>0x00000000</code></td>
    </tr>
    <tr>
        <td>duration of frequency deviation from normal during the accounting period, seconds</td>
        <td><code>20</code></td>
        <td><code>0x00000014</code></td>
    </tr>
    <tr>
        <td>
            <a href="#relay-status">relay status</a>
        </td>
        <td>
            <code>RELAY_STATE</code>: <code>true</code><br>
            <code>RELAY_UBAD</code>: <code>false</code><br>
            <code>RELAY_UNEQ_CURRENT</code>: <code>false</code><br>
            <code>RELAY_OFF_CENTER</code>: <code>false</code><br>
            <code>RELAY_IMAX</code>: <code>false</code><br>
            <code>RELAY_PMAX</code>: <code>false</code><br>
        </td>
        <td><code>0x01</code></td>
    </tr>
    <tr>
        <td>
            <a href="./GetEventStatus.md#status-event-set-1">events status 1</a>
        </td>
        <td>
            <code>CASE_OPEN</code>: <code>false</code><br>
            <code>MAGNETIC_ON</code>: <code>false</code><br>
            <code>PARAMETERS_UPDATE_REMOTE</code>: <code>false</code><br>
            <code>PARAMETERS_UPDATE_LOCAL</code>: <code>false</code><br>
            <code>RESTART</code>: <code>false</code><br>
            <code>ERROR_ACCESS</code>: <code>false</code><br>
            <code>TIME_SET</code>: <code>false</code><br>
            <code>TIME_CORRECT</code>: <code>false</code><br>
        </td>
        <td><code>0x00</code></td>
    </tr>
    <tr>
        <td>
            <a href="./GetEventStatus.md#status-event-set-2">events status 2</a>
        </td>
        <td>
            <code>DEVICE_FAILURE</code>: <code>false</code><br>
            <code>CASE_TERMINAL_OPEN</code>: <code>false</code><br>
            <code>CASE_MODULE_OPEN</code>: <code>false</code><br>
            <code>TARIFF_TABLE_SET</code>: <code>false</code><br>
            <code>TARIFF_TABLE_GET</code>: <code>false</code><br>
            <code>PROTECTION_RESET_EM</code>: <code>false</code><br>
            <code>PROTECTION_RESET_MAGNETIC</code>: <code>false</code><br>
        </td>
        <td><code>0x00</code></td>
    </tr>
    <tr>
        <td>
            <a href="#calibration-flags">calibration flags</a>
        </td>
        <td>
            <code>CALIBRATION</code>: <code>false</code><br>
            <code>HARD_KEY</code>: <code>false</code><br>
        </td>
        <td><code>0x00</code></td>
    </tr>
    <tr>
        <td>current tariff <code>A+</code></td>
        <td><code>1</code></td>
        <td><code>0x01</code></td>
    </tr>
    <tr>
        <td>current tariff <code>A-</code></td>
        <td><code>2</code></td>
        <td><code>0x02</code></td>
    </tr>
    <tr>
        <td>current daylight saving time status</td>
        <td><code>summer</code></td>
        <td><code>0x01</code></td>
    </tr>
</table>

Command hex dump: `39 1f 01001001 00000078 00000079 0000001e 00000000 00000014 01 00 00 00 01 02 01`


## See also

* [Access level](../basics.md#command-access-level)
* [Event status](./GetEventStatus.md#status-event-set-1)
* [Event status 2](./GetEventStatus.md#status-event-set-2)
