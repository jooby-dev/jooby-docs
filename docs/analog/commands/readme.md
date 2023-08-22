# Commands

There are `2` types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

| ID       | Name                                                | Description                                                                  |
| -------- | --------------------------------------------------- | ---------------------------------------------------------------------------- |
| `0x02`   | [SetTime2000](./SetTime2000.md#request)             | Request to correct device time.                                              |
| `0x03`   | [SetParameter](./SetParameter.md#request)           | Request to change device parameter.                                          |
| `0x04`   | [GetParameter](./GetParameter.md#request)           | Request to get device parameter.                                             |
| `0x05`   | [GetArchiveHours](./GetArchiveHours.md#request)     | Request to get the archive data of hourly consumption.                       |
| `0x06`   | [GetArchiveDays](./GetArchiveDays.md#request)       | Request to get the archive of daily data from the pulse counter sensor.      |
| `0x07`   | [GetCurrent](./GetCurrent.md#request)               | Request to get pulse counter readings from the sensor.                       |
| `0x0b`   | [GetArchiveEvents](./GetArchiveEvents.md#request)   | Request to get a events from archive.                                        |
| `0x0c`   | [CorrectTime2000](./CorrectTime2000.md#request)     | Request to correct device time by up to 127 seconds.                         |
| `0x14`   | [GetStatus](./GetStatus.md#request)                 | Request to get status information from the sensor.                           |
| `0x18`   | [GetCurrentMC](./GetCurrentMC.md#request)           | Request to get current pulse counter value.                                  |
| `0x19`   | [SoftRestart](./SoftRestart.md#request)             | Request to restart a device.                                                 |
| `0x1a`   | [GetArchiveHoursMC](./GetArchiveHoursMC.md#request) | Request to get a hour values from archive.                                   |
| `0x1b`   | [GetArchiveDaysMC](./GetArchiveDaysMC.md#request)   | Request to get a day values from archive.                                    |
| `0x1f02` | [GetLmicInfo](./GetLmicInfo.md#request)             | Request to get LMiC (IBM LoRaWAN in C) information.                          |
| `0x1f0f` | [GetExAbsCurrentMC](./GetExAbsCurrentMC.md#request) | Request to receive current consumption absolute values from device channels. |


## Uplink commands

| ID       | Name                                                 | Description                                                                                                                                       |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x02`   | [SetTime2000](./SetTime2000.md#response)             | Response to the [SetTime2000](./SetTime2000.md#request) downlink command.                                                                         |
| `0x03`   | [SetParameter](./SetParameter.md#response)           | Response to [SetParameter](./SetParameter.md#request) downlink command.                                                                           |
| `0x04`   | [GetParameter](./GetParameter.md#response)           | Response to [GetParameter](./GetParameter.md#request) downlink command.                                                                           |
| `0x05`   | [GetArchiveHours](./GetArchiveHours.md#response)     | Response to [GetArchiveHours](./GetArchiveHours.md#request) downlink command.                                                                     |
| `0x06`   | [GetArchiveDays](./GetArchiveDays.md#response)       | Response to [GetArchiveDays](./GetArchiveDays.md#request) downlink command.                                                                       |
| `0x07`   | [GetCurrent](./GetCurrent.md#response)               | Response to [GetCurrent](./GetCurrent.md#request) downlink command.                                                                               |
| `0x09`   | [Time2000](./uplink/Time2000.md)                     | Current device time.                                                                                                                              |
| `0x0b`   | [GetArchiveEvents](./GetArchiveEvents.md#response)   | Response to the [GetArchiveEvents](./GetArchiveEvents.md#request) downlink command.                                                               |
| `0x0c`   | [CorrectTime2000](./CorrectTime2000.md#response)     | Response to the [CorrectTime2000](./CorrectTime2000.md#request) downlink command.                                                                 |
| `0x14`   | [Status](./GetStatus.md#response)                    | Response to the [GetStatus](./GetStatus.md#request) downlink command or current device status information.                                        |
| `0x15`   | [NewEvent](./uplink/NewEvent.md)                     | Info of the device event.                                                                                                                         |
| `0x16`   | [DayMC](./uplink/DayMC.md)                           | Pulse counter data on billing hour.                                                                                                               |
| `0x17`   | [HourMC](./uplink/HourMC.md)                         | Pulse counter data, accumulated on a hour basis.                                                                                                  |
| `0x18`   | [CurrentMC](./GetCurrentMC.md#response)              | Response to the [GetCurrentMC](./GetCurrentMC.md#request) downlink command or current pulse counter value.                                        |
| `0x19`   | [SoftRestart](./SoftRestart.md#response)             | Response to the [SoftRestart](./SoftRestart.md#request) downlink command.                                                                         |
| `0x1a`   | [GetArchiveHoursMC](./GetArchiveHoursMC.md#response) | Response to the [GetArchiveHoursMC](./GetArchiveHoursMC.md#request) downlink command.                                                             |
| `0x1b`   | [GetArchiveDaysMC](./GetArchiveDaysMC.md#response)   | Response to the [GetArchiveDaysMC](./GetArchiveDaysMC.md#request) downlink command.                                                               |
| `0x1f02` | [GetLmicInfo](./GetLmicInfo.md#response)             | Response to the [GetLmicInfo](./GetLmicInfo.md#request) downlink command.                                                                         |
| `0x1f0a` | [ExAbsHourMC](./uplink/ExAbsHourMC.md)               | Absolute values from device channels for the specified hour and hourly difference.                                                                |
| `0x1f0b` | [ExAbsDayMC](./uplink/ExAbsDayMC.md)                 | Absolute values from device channels for the previous day's billing hour.                                                                         |
| `0x1f0f` | [ExAbsCurrentMC](./GetExAbsCurrentMC.md#response)    | Response to the [GetExAbsCurrentMC](./GetExAbsCurrentMC.md#request) downlink command or current consumption absolute values from device channels. |
| `0x20`   | [Day](./uplink/Day.md)                               | Contains complete pulse counter data for the specified day.                                                                                       |
| `0x40`   | [Hour](./uplink/Hour.md)                             | Contains the complete pulse counter value for the specified hour and the hourly difference in readings.                                           |
| `0x60`   | [LastEvent](./uplink/LastEvent.md)                   | Info of the last device event sequence number and the status bits.                                                                                |
