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

| ID     | Name            | Description                                                                       |
| ------ | --------------- | --------------------------------------------------------------------------------- |
| `0x01` | `MAGNET_ON`     | Magnet is used for more than 20 seconds.                                          |
| `0x02` | `MAGNET_OFF`    | Magnetic interference is removed.                                                 |
| `0x03` | `ACTIVATE`      | The device has been activated.                                                    |
| `0x04` | `DEACTIVATE`    | Device deactivation. Termination of frame transmission over the air.              |
| `0x05` | `BATTERY_ALARM` | The sensor has reset due to low battery voltage.                                  |
| `0x06` | `CAN_OFF`       | The container has tipped over.                                                    |
| `0x07` | `INSERT`        | Device installation in the gas meter.                                             |
| `0x08` | `REMOVE`        | Device removal from gas meter.                                                    |
| `0x09` | `COUNTER_OVER`  | The pulse counter has overflowed. The number of pulses has exceeded `4294967295`. |
| `0x0a` | `SET_TIME`      | Setting the device time.                                                          |
| `0x0b` | `ACTIVATE_MTX`  |                                                                                   |
| `0x0c` | `CONNECT`       |                                                                                   |
| `0x0d` | `DISCONNECT`    |                                                                                   |
| `0x0e` | `DEPASS_DONE`   | Device battery depassivation.                                                     |
| `0x0f` | `EV_OPTOLOW`    |                                                                                   |
| `0x10` | `EV_OPTOFLASH`  |                                                                                   |
| `0x11` | `EV_MTX`        |                                                                                   |
| `0x12` | `EV_REJOIN`     |                                                                                   |


## Hardware types

| ID     | Name     | Description                                                                             |
| ------ | -------- | --------------------------------------------------------------------------------------- |
| `0x01` | GAZM3    | GAS RM on cpu STM32L15x - no longer in production, over 10,000 were produced.           |
| `0x02` | GAZM0    | GAS RM on cpu STM32L05x - no longer in production, several thousand produced.           |
| `0x03` | GAZM0NEW | GAS RM on cpu STM32L05x - test batch.                                                   |
| `0x04` | NOVATOR  | RM for novator. <br> (2 channels)                                                       |
| `0x05` | IMP2EU   | RM with 2 ports, no longer in production. <br> (2 channels)                             |
| `0x06` | IMP4EU   | RM with 4 ports, EU868. <br> (4 channels)                                               |
| `0x07` | MTXLORA  | RM installed inside MTX meters.                                                         |
| `0x08` | IMP2AS   | RM with 2 ports for the Asian region, AS923, no longer in production. <br> (2 channels) |
| `0x09` | IMP2IN   | RM with 2 ports for the Asian region, IN865, no longer in production. <br> (2 channels) |
| `0x0a` | IMP4IN   | RM with 4 ports for the Asian region, IN865, no longer in production. <br> (4 channels) |
| `0x0b` | ELIMP    | Single-port module with supply 220 V. Class C. <br> (1 channel)                         |
| `0x0c` | GAZWLE   | GAS RM on cpu STM32WLE5.                                                                |
| `0x0d` | WATER    | RM for ultrasonic water meter (Rozhok laboratory).                                      |
| `0x0e` | PLC2LORA | Combined PLC2 & LORA RM for MTX electric energy meter.                                  |
