# Basics

## Device time management

A device sends its time as a 4 bytes unsigned integer value with [Time2000](./commands/uplink/Time2000.md) event.
It's amount of seconds since year 2000.
This time should be corrected periodically with one of the following commands: [SetTime2000](./commands/SetTime2000.md) and [CorrectTime2000](./commands/CorrectTime2000.md).

[SetTime2000](./commands/SetTime2000.md) mostly intended for initial time setup when time correction is more than `127` seconds.

[CorrectTime2000](./commands/CorrectTime2000.md) is for minor time corrections (less than `127` seconds).

It is recommended to maintain time lag no more than 30 seconds.
