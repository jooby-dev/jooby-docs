# Basics

## Device time management

A device sends its time as a 4 bytes unsigned integer value with [Time2000](./commands/uplink/Time2000.md) event.
It's amount of seconds since year 2000.
This time should be corrected periodically with one of the following commands: [CorrectTime](./commands/CorrectTime.md) and [CorrectTimeSmall](./commands/CorrectTimeSmall.md).

[CorrectTime](./commands/CorrectTime.md) mostly intended for initial time setup when time correction is more than `127` seconds.

[CorrectTimeSmall](./commands/CorrectTimeSmall.md) is for minor time corrections (less than `127` seconds).

It is recommended to maintain time lag no more than 30 seconds.
