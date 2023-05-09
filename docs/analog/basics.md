# Basics

## Device time management

A device sends its time as a 4 bytes unsigned integer value with [Time2000](./commands/uplink/Time2000.md) event.
The time is represented in a special [time 2000](./types.md#time-2000) format.
This time should be corrected periodically with one of the following commands: [SetTime2000](./commands/SetTime2000.md) and [CorrectTime2000](./commands/CorrectTime2000.md).

[SetTime2000](./commands/SetTime2000.md) is mostly intended for initial time setup when the time difference (in seconds) is out of range `[-127..+127]`.

[CorrectTime2000](./commands/CorrectTime2000.md) is for minor time corrections when the time difference (in seconds) is in range `[-127..+127]`.

There may be some hour values loss in case of negative time correction.
It is recommended to maintain time lag no more than 30 seconds.


## Device events

All events in the device are stored in the event archive.
The capacity of the archive is at least 256 events and no more than 512 events.
The event time, event ID, and [LastEvent sequence number](./commands/uplink/LastEvent.md#sequence-number) are recorded in the archive.
The sequence number is incremented with each new event.
This number is transmitted to the server using the [LastEvent](./commands/uplink/LastEvent.md) command, which is added to each `uplink` frame transmitted without a request.
There is no message prioritization in the archive.
Events are recorded in a cycle.
Archives can be requested for the latest events, the oldest events, and events starting from a certain time.

| ID     | Name                | Description                                                                       |
| ------ | ------------------- | --------------------------------------------------------------------------------- |
| `0x01` | `MAGNET_ON`         | Magnet is used for more than 20 seconds.                                          |
| `0x02` | `MAGNET_OFF`        | Magnetic interference is removed.                                                 |
| `0x03` | `ACTIVATE`          | The device has been activated.                                                    |
| `0x04` | `DEACTIVATE`        | Device deactivation. Termination of frame transmission over the air.              |
| `0x05` | `BATTERY_ALARM`     | The sensor has reset due to low battery voltage. Outdated.                        |
| `0x06` | `CAN_OFF`           | The container has tipped over. Outdated.                                          |
| `0x07` | `INSERT`            | Device installation in the gas meter.                                             |
| `0x08` | `REMOVE`            | Device removal from gas meter.                                                    |
| `0x09` | `COUNTER_OVER`      | The pulse counter has overflowed. The number of pulses has exceeded `4294967295`. |
| `0x0a` | `SET_TIME`          | Setting the device time.                                                          |
| `0x0b` | `ACTIVATE_MTX`      | Activation of the module in the electric energy meter (restart or power supply).  |
| `0x0c` | `CONNECT`           | Connecting a plug to a 2-port module.                                             |
| `0x0d` | `DISCONNECT`        | Disconnecting a connector from a 2-port module.                                   |
| `0x0e` | `DEPASS_DONE`       | Device battery depassivation.                                                     |
| `0x0f` | `OPTOLOW`           | Low signal level from photodiode (`NOVATOR`).                                     |
| `0x10` | `OPTOFLASH`         | Photodiode overexposure (`NOVATOR`).                                              |
| `0x11` | `MTX`               | MTX electric energy meter event.                                                  |
| `0x12` | `JOIN_ACCEPT`       | Receiving `JOINACCEPT` from NS in OTAA mode (not implemented).                    |
| `0x13` | `WATER_EVENT`       | Ultrasonic water meter event.                                                     |
| `0x14` | `WATER_NO_RESPONSE` | No response from ultrasonic water meter.                                          |
| `0x15` | `OPTOSENSOR_ERROR`  | Optical sensor error.                                                             |

## Hardware types

<table>
    <thead>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Model</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>0x01</code></td>
            <td><code>GAZI1</code></td>
            <td>
                <code>Jooby RM GM-E</code> <br>
                <code>Jooby RM GM-M</code>
            </td>
            <td>Based on CPU <code>STM32L15x</code> (no longer in production).</td>
        </tr>
        <tr>
            <td><code>0x02</code></td>
            <td><code>GAZI2</code></td>
            <td>
                <code>Jooby RM GM-E</code>
            </td>
            <td>Based on CPU <code>STM32L05x</code> (no longer in production).</td>
        </tr>
        <tr>
            <td><code>0x03</code></td>
            <td><code>GAZI3</code></td>
            <td>
                <code>Jooby RM GM-E</code> <br>
                <code>Jooby RM GM-M</code> <br>
                <code>Jooby RM GM-S</code> <br>
                <code>Jooby RM GM-E_ext</code> <br>
                <code>Jooby RM GM-M_ext</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMSG10 105 EU</code>
            </td>
            <td>Based on CPU <code>STM32L05x</code>.
            </td>
        </tr>
        <tr>
            <td><code>0x04</code></td>
            <td><code>NOVATOR</code></td>
            <td>
                <code>Jooby RM O-WM-N</code> <br>
                <code>Jooby Aquaris RMS LoRaWAN WONO10 203 EU</code>
            </td>
            <td>Based on CPU <code>STM32WLE5</code>.</td>
        </tr>
        <tr>
            <td><code>0x05</code></td>
            <td><code>IMP2EU</code></td>
            <td>
                Radio module with 2 pulse inputs
            </td>
            <td>Based on CPU <code>STM32L051</code> (no longer in production).</td>
        </tr>
        <tr>
            <td><code>0x06</code></td>
            <td><code>IMP4EU</code></td>
            <td>
                <code>Jooby RM 4PI</code> <br>
                <code>Jooby OMNI RM LoRaWAN 4PI 200 EU</code> <br>
                <code>Jooby OMNI RM LoRaWAN 4PI 202 EU</code>
            </td>
            <td>Based on CPU <code>STM32WLE5</code>.</td>
        </tr>
        <tr>
            <td><code>0x07</code></td>
            <td><code>MTXLORA</code></td>
            <td></td>
            <td>
                RM installed inside MTX meters. <br>
                Based on <code>STM32L051</code>, <code>STM32L071</code> (no longer in production) and <code>STM32WLE5</code>.
            </td>
        </tr>
        <tr>
            <td><code>0x08</code></td>
            <td><code>IMP2AS</code></td>
            <td></td>
            <td>RM with 2 ports for the Asian region, <code>AS923</code> (no longer in production).</td>
        </tr>
        <tr>
            <td><code>0x09</code></td>
            <td><code>IMP2IN</code></td>
            <td></td>
            <td>RM with 2 ports for the Indian region, <code>IN865</code> (no longer in production).</td>
        </tr>
        <tr>
            <td><code>0x0a</code></td>
            <td><code>IMP4IN</code></td>
            <td></td>
            <td>RM with 4 ports for the Indian region, <code>IN865</code> (no longer in production).</td>
        </tr>
        <tr>
            <td><code>0x0b</code></td>
            <td><code>ELIMP</code></td>
            <td>
                <code>Jooby ELECTRA RM LoRaWAN 1PI 100 EU</code>
            </td>
            <td>Single-port module with supply <code>220V</code>. Class <code>C</code>. Based on CPU <code>STM32WLE5</code>.</td>
        </tr>
        <tr>
            <td><code>0x0c</code></td>
            <td><code>GAZIC</code></td>
            <td>
                <code>Jooby RM GM-E</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMEL10 100 EU</code> <br>
                <code>Jooby RM GM-M</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMME10 103 EU</code> <br>
                <code>Jooby RM GM-E_ext</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMEL10 102 EU</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMEL10 106 EU</code> <br>
                <code>Jooby RM GM-M_ext</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMME10 104 EU</code> <br>
                <code>Jooby EPHIR RMS LoRaWAN GMME10 107 EU</code>
            </td>
            <td>Based on CPU <code>STM32WLE5</code>.</td>
        </tr>
        <tr>
            <td><code>0x0f</code></td>
            <td><code>IMP4AS</code></td>
            <td>
                <code>Jooby RM 4PI</code> <br>
                <code>Jooby OMNI RM LoRaWAN 4PI 200 AS</code> <br>
                <code>Jooby OMNI RM LoRaWAN 4PI 202 AS</code>
            </td>
        </tr>
    </tbody>
</table>
