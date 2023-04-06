# Basics

## Device time management

A device sends its time as a 4 bytes unsigned integer value with [Time2000](./commands/uplink/Time2000.md) event.
It's amount of seconds since year 2000.
This time should be corrected periodically with one of the following commands: [SetTime2000](./commands/SetTime2000.md) and [CorrectTime2000](./commands/CorrectTime2000.md).

[SetTime2000](./commands/SetTime2000.md) is mostly intended for initial time setup when the time difference (in seconds) is in range `[-127..+127]`.

[CorrectTime2000](./commands/CorrectTime2000.md) is for minor time corrections when the time difference (in seconds) is out of range `[-127..+127]`.

There may be some hour values loss in case of negative time correction.
It is recommended to maintain time lag no more than 30 seconds.
