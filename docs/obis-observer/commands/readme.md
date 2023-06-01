# Commands

There are `2` types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

| ID     | Name                                                          | Description                                                      |
| ------ | ------------------------------------------------------------- | ---------------------------------------------------------------- |
| `0x01` | [GetShortNames](./GetShortNames.md#request)                   | Request to get the short names of the specific OBIS code.        |
| `0x03` | [SetShortName](./SetShortName.md#request)                     | Request to set the short name for the specific OBIS code.        |
| `0x05` | [AddShortNameProfile](./AddShortNameProfile.md#request)       | Request to add ShortName profile.                                |
| `0x07` | [RemoveShortNameProfile](./RemoveShortNameProfile.md#request) | Request to remove ShortName profile.                             |
| `0x09` | [GetShortNameProfile](./GetShortNameProfile.md#request)       | Request to get ShortName profile.                                |
| `0x0b` | [GetShortNameInfo](./GetShortNameInfo.md#request)             | Request to get ShortName information. Related OBIS and profile.. |
| `0x0d` | [GetArchiveProfile](./GetArchiveProfile.md#request)           | Request to get archive profile.                                  |
| `0x0f` | [SetArchiveProfile](./SetArchiveProfile.md#request)           | Request to set archive profile.                                  |
| `0x11` | [ReadArchive](./ReadArchive.md#request)                       | Request to read the archive.                                     |
| `0x13` | [SetSerialPort](./SetSerialPort.md#request)                   | Request to set serial port parameters.                           |
| `0x15` | [GetContentByObis](./GetContentByObis.md#request)             | Request to get OBIS content.                                     |
| `0x17` | [GetContentByShortName](./GetContentByShortName.md#request)   | Request to restart the device.                                   |
| `0x1c` | [Reboot](./Reboot.md#request)                                 | Request to get OBIS content.                                     |
| `0x1e` | [GetLorawanInfo](./GetLorawanInfo.md#request)                 | Request to get LoRaWAN information.                              |
| `0x20` | [GetDeviceInfo](./GetDeviceInfo.md#request)                   | Request to get information about device.                         |


## Uplink commands

| ID     | Name                                                                                | Description                                                                                                       |
| ------ | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `0x02` | [GetShortNames](./GetShortNames#response)                                           | Response to the [GetShortNames](./GetShortNames.md#request) downlink command.                                     |
| `0x04` | [SetShortName](./SetShortName#response)                                             | Response to the [SetShortName](./SetShortName.md#request) downlink command.                                       |
| `0x06` | [AddShortNameProfile](./AddShortNameProfile#response)                               | Response to the [AddShortNameProfile](./AddShortNameProfile.md#request) downlink command.                         |
| `0x08` | [RemoveShortNameProfile](./RemoveShortNameProfile#response)                         | Response to the [RemoveShortNameProfile](./RemoveShortNameProfile.md#request) downlink command.                   |
| `0x0a` | [GetShortNameProfile](./GetShortNameProfile#response)                               | Response to the [GetShortNameProfile](./GetShortNameProfile.md#request) downlink command.                         |
| `0x0c` | [GetShortNameInfo](./GetShortNameInfo#response)                                     | Response to the [GetShortNameInfo](./GetShortNameInfo.md#request) downlink command.                               |
| `0x0e` | [GetArchiveProfile](./GetArchiveProfile#response)                                   | Response to the [GetArchiveProfile](./GetArchiveProfile.md#request) downlink command.                             |
| `0x10` | [SetArchiveProfile](./SetArchiveProfile#response)                                   | Response to the [SetArchiveProfile](./SetArchiveProfile.md#request) downlink command.                             |
| `0x12` | [ReadArchive](./ReadArchive#response)                                               | Response to the [ReadArchive](./ReadArchive.md#request) downlink command.                                         |
| `0x14` | [SetSerialPort](./SetSerialPort#response)                                           | Response to the [SetSerialPort](./SetSerialPort.md#request) downlink command.                                     |
| `0x16` | [GetContentByObis](./GetContentByObis#response)                                     | Response to the [GetContentByObis](./GetContentByObis.md#request) downlink command.                               |
| `0x18` | [GetContentByShortName](./GetContentByShortName#response-with-float-content)        | Response to the [GetContentByShortName](./GetContentByShortName.md#request) downlink command with float content.  |
| `0x19` | [GetContentByShortNameString](./GetContentByShortName#response-with-string-content) | Response to the [GetContentByShortName](./GetContentByShortName.md#request) downlink command with string content. |
| `0x1a` | [ObservationReport](./uplink/ObservationReport.md#event-with-float-content)         | Content of the OBIS codes that were captured with float content.                                                  |
| `0x1b` | [ObservationReportString](./uplink/ObservationReport.md#event-with-string-content)  | Content of the OBIS codes that were captured with string content.                                                 |
| `0x1d` | [Reboot](./Reboot.md#response)                                                      | Response to the [Reboot](./Reboot.md#request) downlink command.                                                   |
| `0x1f` | [GetLorawanInfo](./GetLorawanInfo.md#response)                                      | Response to the [GetLorawanInfo](./GetLorawanInfo.md#request) downlink command.                                   |
| `0x21` | [GetDeviceInfo](./GetDeviceInfo.md#response)                                        | Response to the [GetDeviceInfo](./GetDeviceInfo.md#request) downlink command.                                     |

**Note**

All number fields in the commands are transmitted in big-endian format.
