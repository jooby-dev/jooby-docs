# Basics

## Device time management

A device sends its time as a 4 bytes unsigned integer value with [Time2000](./commands/uplink/Time2000.md) event.
It's amount of seconds since year 2000.
This time should be corrected periodically with one of the following commands: [SetTime2000](./commands/SetTime2000.md) and [CorrectTime2000](./commands/CorrectTime2000.md).

[SetTime2000](./commands/SetTime2000.md) is mostly intended for initial time setup when the time difference (in seconds) is in range `[-127..+127]`.

[CorrectTime2000](./commands/CorrectTime2000.md) is for minor time corrections when the time difference (in seconds) is out of range `[-127..+127]`.

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

 ID     | Name               | Description
--------|--------------------|-------------
 `0x01` | `MAGNET_ON`        | Magnet is used for more than 20 seconds.
 `0x02` | `MAGNET_OFF`       | Magnetic interference is removed.
 `0x03` | `ACTIVATE`         | The device has been activated.
 `0x04` | `DEACTIVATE`       | Device deactivation. Termination of frame transmission over the air.
 `0x07` | `INSERT`           | Device installation in the gas meter.
 `0x08` | `REMOVE`           | Device removal from gas meter.
 `0x09` | `COUNTER_OVER`     | The pulse counter has overflowed. The number of pulses has exceeded `4294967295`.
 `0x0a` | `SET_TIME`         | Setting the device time.
 `0x0e` | `DEPASS_DONE`      | Device battery depassivation.
