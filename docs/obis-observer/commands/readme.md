# Commands

There are `2` types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

| ID     | Name                                                          | Description                                                     |
| ------ | ------------------------------------------------------------- | --------------------------------------------------------------- |
| `0x01` | [GetObisIdList](./GetObisIdList.md#request)                   | Request to get the obis id list for the specific OBIS code.     |
| `0x03` | [SetObisId](./SetObisId.md#request)                           | Request to set the OBIS id for the specific OBIS code.          |
| `0x05` | [AddObisProfile](./AddObisProfile.md#request)                 | Request to add OBIS profile.                                    |
| `0x07` | [RemoveObisProfile](./RemoveObisProfile.md#request)           | Request to remove OBIS profile.                                 |
| `0x09` | [GetObisProfile](./GetObisProfile.md#request)                 | Request to get OBIS profile.                                    |
| `0x0b` | [GetObisInfo](./GetObisInfo.md#request)                       | Request to get OBIS information. Related OBIS and profile..     |
| `0x0d` | [GetMeterArchiveProfile](./GetMeterArchiveProfile.md#request) | Request to get archive profile.                                 |
| `0x0f` | [SetMeterArchiveProfile](./SetMeterArchiveProfile.md#request) | Request to set archive profile.                                 |
| `0x11` | [ReadMeterArchive](./ReadMeterArchive.md#request)             | Request to read the archive  for the specific meter.            |
| `0x13` | [SetSerialPort](./SetSerialPort.md#request)                   | Request to set serial port parameters.                          |
| `0x15` | [GetObisContent](./GetObisContent.md#request)                 | Request to get OBIS content.                                    |
| `0x17` | [GetObisContentById](./GetObisContentById.md#request)         | Request to get OBIS content.                                    |
| `0x1c` | [Reboot](./Reboot.md#request)                                 | Request to restart the device.                                  |
| `0x1e` | [GetLorawanInfo](./GetLorawanInfo.md#request)                 | Request to get LoRaWAN information.                             |
| `0x20` | [GetObserverInfo](./GetObserverInfo.md#request)               | Request to get information about observer.                      |
| `0x22` | [GetMeterDate](./GetMeterDate.md#request)                     | Request to get the current date and time on the specific meter. |
| `0x24` | [GetLorawanState](./GetLorawanState.md#request)               | Request to get LoRaWAN state.                                   |
| `0x26` | [GetMeterReadoutState](./GetMeterReadoutState.md#request)     | Request to get readout state.                                   |
| `0x28` | [GetMeterArchiveState](./GetMeterArchiveState.md#request)     | Request to get archive state for the specific meter.            |
| `0x2a` | [UpdateImageWrite](./UpdateImageWrite.md#request)             | Request to write the block of the new image to the device.      |
| `0x2c` | [UpdateImageVerify](./UpdateImageVerify.md#request)           | Request to verify the update image on the device.               |
| `0x2e` | [UpdateRun](./UpdateRun.md#request)                           | Request to run the update on the device.                        |

## Uplink commands

| ID     | Name                                                                             | Description                                                                                                 |
| ------ | -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `0x02` | [GetObisIdList](./GetObisIdList.md#response)                                     | Response to the [GetObisIdList](./GetObisIdList.md#request) downlink command.                               |
| `0x04` | [SetObisId](./SetObisId.md#response)                                             | Response to the [SetObisId](./SetObisId.md#request) downlink command.                                       |
| `0x06` | [AddObisProfile](./AddObisProfile.md#response)                                   | Response to the [AddObisProfile](./AddObisProfile.md#request) downlink command.                             |
| `0x08` | [RemoveObisProfile](./RemoveObisProfile.md#response)                             | Response to the [RemoveObisProfile](./RemoveObisProfile.md#request) downlink command.                       |
| `0x0a` | [GetObisProfile](./GetObisProfile.md#response)                                   | Response to the [GetObisProfile](./GetObisProfile.md#request) downlink command.                             |
| `0x0c` | [GetObisInfo](./GetObisInfo.md#response)                                         | Response to the [GetObisInfo](./GetObisInfo.md#request) downlink command.                                   |
| `0x0e` | [GetMeterArchiveProfile](./GetMeterArchiveProfile.md#response)                   | Response to the [GetMeterArchiveProfile](./GetMeterArchiveProfile.md#request) downlink command.             |
| `0x10` | [SetMeterArchiveProfile](./SetMeterArchiveProfile.md#response)                   | Response to the [SetMeterArchiveProfile](./SetMeterArchiveProfile.md#request) downlink command.             |
| `0x12` | [ReadMeterArchive](./ReadMeterArchive.md#response)                               | Response to the [ReadMeterArchive](./ReadArchive.md#request) downlink command.                              |
| `0x14` | [SetSerialPort](./SetSerialPort.md#response)                                     | Response to the [SetSerialPort](./SetSerialPort.md#request) downlink command.                               |
| `0x16` | [GetObisContent](./GetObisContent.md#response)                                   | Response to the [GetObisContent](./GetObisContent.md#request) downlink command.                             |
| `0x18` | [GetObisContentById](./GetObisContentById.md#response-with-float-content)        | Response to the [GetObisContentById](./GetObisContentById.md#request) downlink command with float content.  |
| `0x19` | [GetObisContentByIdString](./GetObisContentById.md#response-with-string-content) | Response to the [GetObisContentById](./GetObisContentById.md#request) downlink command with string content. |
| `0x1a` | [ObservationReport](./uplink/ObservationReport.md)                               | Content of the OBIS codes that were captured with float content.                                            |
| `0x1b` | [ObservationReportString](./uplink/ObservationReportString.md)                   | Content of the OBIS codes that were captured with string content.                                           |
| `0x1d` | [Reboot](./Reboot.md#response)                                                   | Response to the [Reboot](./Reboot.md#request) downlink command.                                             |
| `0x1f` | [GetLorawanInfo](./GetLorawanInfo.md#response)                                   | Response to the [GetLorawanInfo](./GetLorawanInfo.md#request) downlink command.                             |
| `0x21` | [GetObserverInfo](./GetObserverInfo.md#response)                                 | Response to the [GetObserverInfo](./GetObserverInfo.md#request) downlink command.                           |
| `0x23` | [GetMeterDate](./GetMeterDate.md#response)                                       | Response to the [GetMeterDate](./GetMeterDate.md#request) downlink command.                                 |
| `0x25` | [GetLorawanState](./GetLorawanState.md#response)                                 | Response to the [GetLorawanState](./GetLorawanState.md#request) downlink command.                           |
| `0x27` | [GetMeterReadoutState](./GetMeterReadoutState.md#response)                       | Response to the [GetMeterReadoutState](./GetMeterReadoutState.md#request) downlink command.                 |
| `0x29` | [GetMeterArchiveState](./GetMeterArchiveState.md#response)                       | Response to the [GetMeterArchiveState](./GetMeterArchiveState.md#request) downlink command.                 |
| `0x2b` | [UpdateImageWrite](./UpdateImageWrite.md#response)                               | Response to the [UpdateImageWrite](./UpdateImageWrite.md#request) downlink command.                         |
| `0x2d` | [UpdateImageVerify](./UpdateImageVerify.md#response)                             | Response to the [UpdateImageVerify](./UpdateImageVerify.md#request) downlink command.                       |
| `0x2f` | [UpdateRun](./UpdateRun.md#response)                                             | Response to the [UpdateRun](./UpdateRun.md#request) downlink command.                                       |


**Note**

All number fields in the commands are transmitted in big-endian format.
