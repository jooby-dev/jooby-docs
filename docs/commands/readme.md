# Commands

There are 2 types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

| ID       | Name                                                | Description                                                                  |
| -------- | --------------------------------------------------- | ---------------------------------------------------------------------------- |
| `0x02`   | [SetTime2000](./SetTime2000.md#request)             | Request to correct device time.                                              |
| `0x03`   | [SetParameter](./SetParameter.md#request)           | Request to change device parameter.                                          |
| `0x0c`   | [CorrectTime2000](./CorrectTime2000.md#request)     | Request to correct device time by up to 127 seconds.                         |
| `0x14`   | [GetStatus](./GetStatus.md#request)                 | Request to get status information from the sensor.                           |
| `0x18`   | [GetCurrentMC](./GetCurrentMC.md#request)           | Request to get current pulse counter value for multichannel devices.         |
| `0x19`   | [SoftRestart](./SoftRestart.md#request)             | Request to restart a device.                                                 |
| `0x1f02` | [GetLmicInfo](./GetLmicInfo.md#request)             | Request to get LMiC (IBM LoRaWAN in C) information.                          |
| `0x1f0f` | [GetExAbsCurrentMC](./GetExAbsCurrentMC.md#request) | Request to receive current consumption absolute values from device channels. |


## Uplink commands

| ID       | Name                                              | Description                                                                                                                                       |
| -------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x02`   | [SetTime2000](./SetTime2000.md#response)          | Response to the [SetTime2000](./SetTime2000.md#request) downlink command.                                                                         |
| `0x03`   | [SetParameter](./SetParameter.md#response)        | Response to [SetParameter](./SetParameter.md#request) downlink command.                                                                           |
| `0x09`   | [Time2000](./uplink/Time2000.md)                  | Current device time.                                                                                                                              |
| `0x0c`   | [CorrectTime2000](./CorrectTime2000.md#response)  | Response to the [CorrectTime2000](./CorrectTime2000.md#request) downlink command.                                                                 |
| `0x14`   | [Status](./GetStatus.md#response)                 | Response to the [GetStatus](./GetStatus.md#request) downlink command or current device status information.                                        |
| `0x16`   | [DayMC](./uplink/DayMC.md)                        | Pulse counter data of a multichannel sensor on billing hour.                                                                                      |
| `0x17`   | [HourMC](./uplink/HourMC.md)                      | Pulse counter data of a multichannel sensor, accumulated on a hour basis.                                                                         |
| `0x18`   | [CurrentMC](./GetCurrentMC.md#response)           | Response to the [GetCurrentMC](./GetCurrentMC.md#request) downlink command or current pulse counter value for multichannel devices.               |
| `0x19`   | [SoftRestart](./SoftRestart.md#response)          | Response to the [SoftRestart](./SoftRestart.md#request) downlink command.                                                                         |
| `0x1f02` | [GetLmicInfo](./GetLmicInfo.md#response)          | Response to the [GetLmicInfo](./GetLmicInfo.md#request) downlink command.                                                                         |
| `0x1f0b` | [ExAbsDayMC](./ExAbsDayMC.md)                     | Absolute values from device channels for the previous day's billing hour.                                                                         |
| `0x1f0f` | [ExAbsCurrentMC](./GetExAbsCurrentMC.md#response) | Response to the [GetExAbsCurrentMC](./GetExAbsCurrentMC.md#request) downlink command or current consumption absolute values from device channels. |
| `0x60`   | [LastEvent](./uplink/LastEvent.md)                | Info of the last device event sequence number and the status bits.                                                                                |
