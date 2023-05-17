# Commands

There are 2 types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

| ID     | Name                                                          | Description                                                      |
| ------ | ------------------------------------------------------------- | ---------------------------------------------------------------- |
| `0x01` | [GetShortName](./GetShortName.md#request)                     | Request to get the short name of the specific OBIS code.         |
| `0x02` | [SetShortName](./SetShortName.md#request)                     | Request to set the short name for the specific OBIS code.        |
| `0x03` | [AddShortNameProfile](./AddShortNameProfile.md#request)       | Request to add ShortName profile.                                |
| `0x04` | [RemoveShortNameProfile](./RemoveShortNameProfile.md#request) | Request to remove ShortName profile.                             |
| `0x05` | [GetShortNameProfile](./GetShortNameProfile.md#request)       | Request to get ShortName profile.                                |
| `0x06` | [GetShortNameInfo](./GetShortNameInfo.md#request)             | Request to get ShortName information. Related OBIS and profile.. |
| `0x07` | [GetArchiveProfile](./GetArchiveProfile.md#request)           | Request to get archive profile.                                  |
| `0x08` | [SetArchiveProfile](./SetArchiveProfile.md#request)           | Request to set archive profile.                                  |
| `0x09` | [ReadArchive](./ReadArchive.md#request)                       | Request to read the archive.                                     |
| `0x0b` | [GetContentByObis](./GetContentByObis.md#request)             | Request to get OBIS content.                                     |
| `0x0c` | [GetContentByShortName](./GetContentByShortName.md#request)   | Request to get OBIS content.                                     |


## Uplink commands

| ID     | Name                                                            | Description                                                                                                       |
| ------ | --------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `0x02` | [GetShortName](./GetShortName#response)                         | Response to the [GetShortName](./GetShortName.md#request) downlink command.                                       |
| `0x02` | [SetShortName](./SetShortName#response)                         | Response to the [SetShortName](./SetShortName.md#request) downlink command.                                       |
| `0x03` | [AddShortNameProfile](./AddShortNameProfile#response)           | Response to the [AddShortNameProfile](./AddShortNameProfile.md#request) downlink command.                         |
| `0x04` | [RemoveShortNameProfile](./RemoveShortNameProfile#response)     | Response to the [RemoveShortNameProfile](./RemoveShortNameProfile.md#request) downlink command.                   |
| `0x05` | [GetShortNameProfile](./GetShortNameProfile#response)           | Response to the [GetShortNameProfile](./GetShortNameProfile.md#request) downlink command.                         |
| `0x06` | [GetShortNameInfo](./GetShortNameInfo#response)                 | Response to the [GetShortNameInfo](./GetShortNameInfo.md#request) downlink command.                               |
| `0x07` | [GetArchiveProfile](./GetArchiveProfile#response)               | Response to the [GetArchiveProfile](./GetArchiveProfile.md#request) downlink command.                             |
| `0x08` | [SetArchiveProfile](./SetArchiveProfile#response)               | Response to the [SetArchiveProfile](./SetArchiveProfile.md#request) downlink command.                             |
| `0x09` | [ReadArchive](./ReadArchive#response)                           | Response to the [ReadArchive](./ReadArchive.md#request) downlink command.                                         |
| `0x0b` | [GetContentByObis](./GetContentByObis#response)                 | Response to the [GetContentByObis](./GetContentByObis.md#request) downlink command.                               |
| `0x0c` | [GetContentByShortName](./GetContentByShortName#response)       | Response to the [GetContentByShortName](./GetContentByShortName.md#request) downlink command with float content.  |
| `0x0d` | [GetContentByShortNameStr](./GetContentByShortNameStr#response) | Response to the [GetContentByShortName](./GetContentByShortName.md#request) downlink command with string content. |
| `0x0e` | [ObservationReport](./uplink/ObservationReport.md)              | Content of the OBIS codes that were captured with float content.                                                  |
| `0x0f` | [ObservationReportStr](./uplink/ObservationReportStr.md)        | Content of the OBIS codes that were captured with string content.                                                 |

**Note**

All number fields in the commands are transmitted in big-endian format.
