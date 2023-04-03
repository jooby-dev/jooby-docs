# Commands

There are 2 types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

 ID     | Name                                            | Description
--------|-------------------------------------------------|-------------
 `0x02` | [SetTime2000](./SetTime2000.md#request)         | Request to correct device time.
 `0x0c` | [CorrectTime2000](./CorrectTime2000.md#request) | Request to correct device time by up to 127 seconds.


## Uplink commands

 ID     | Name                                             | Description
--------|--------------------------------------------------|-------------
 `0x02` | [SetTime2000](./SetTime2000.md#response)         | Response to [SetTime2000](./SetTime2000.md#request) downlink command.
 `0x09` | [Time2000](./uplink/Time2000.md)                 | Current device time.
 `0x0c` | [CorrectTime2000](./CorrectTime2000.md#response) | Response to [CorrectTime2000](./CorrectTime2000.md#request) downlink command.
 `0x16` | [DataDayMul](./uplink/DataDayMul.md)             | Pulse counter data of the multichannel sensor on billing hour.
 `0x17` | [DataHourMul](./uplink/DataHourMul.md)           | Pulse counter data of the multichannel sensor, accumulated on a hour basis.
 `0x18` | [GetCurrentMul](./uplink/GetCurrentMul.md)       | Current pulse counter value for multichannel devices.
