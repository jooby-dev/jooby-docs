# Commands

There are `2` types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)


## Downlink commands

| ID     | Name                                                                  | Description                                                                    |
| ------ | --------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| `0x01` | [GetObserverInfo](./GetObserverInfo.md#request)                       | Request to get information about the observer device.                          |
| `0x03` | [GetObserverCapabilities](./GetObserverCapabilities.md#request)       | Request to get the observer capabilities.                                      |
| `0x05` | [GetObserverUptime](./GetObserverUptime.md#request)                   | Request to get uptime in seconds of the observer device.                       |
| `0x09` | [SetSerialPort](./SetSerialPort.md#request)                           | Request to set serial port parameters.                                         |
| `0x0b` | [SetSingleMode](./SetSingleMode.md#request)                           | Request to set the single or multi mode of the observer device.                |
| `0x0d` | [GetSingleMode](./GetSingleMode.md#request)                           | Request to get the current mode (single or multi mode) of the observer device. |
| `0x0f` | [GetArchiveState](./GetArchiveState.md#request)                       | Request to get archive state.                                                  |
| `0x11` | [ReadMeterArchive](./ReadMeterArchive.md#request)                     | Request to read the meter archive.                                             |
| `0x13` | [ReadMeterArchiveWithDate](./ReadMeterArchiveWithDate.md#request)     | Request to read the meter archive for the specific date.                       |
| `0x20` | [GetLorawanInfo](./GetLorawanInfo.md#request)                         | Request to get LoRaWAN information.                                            |
| `0x22` | [GetLorawanState](./GetLorawanState.md#request)                       | Request to get LoRaWAN state.                                                  |
| `0x24` | [SetLorawanActivationMethod](./SetLorawanActivationMethod.md#request) | Request to set the LoRaWAN activation method OTAA or ABP.                      |
| `0x26` | [Reboot](./Reboot.md#request)                                         | Request to reboot the observer device.                                         |
| `0x30` | [UpdateImageWrite](./UpdateImageWrite.md#request)                     | Request to write the block of the new image to the device.                     |
| `0x32` | [UpdateImageVerify](./UpdateImageVerify.md#request)                   | Request to verify the update image on the device.                              |
| `0x34` | [UpdateRun](./UpdateRun.md#request)                                   | Request to run the update on the device.                                       |
| `0x40` | [GetObisIdList](./GetObisIdList.md#request)                           | Request to get the OBIS id list for the specific meter profile.                |
| `0x42` | [SetupObis](./SetupObis.md#request)                                   | Request to set up the id and OBIS profile for the specific OBIS code.          |
| `0x44` | [RemoveObis](./RemoveObis.md#request)                                 | Request to remove OBIS from service.                                           |
| `0x46` | [AddObisProfile](./AddObisProfile.md#request)                         | Request to add OBIS profile.                                                   |
| `0x4a` | [GetObisProfile](./GetObisProfile.md#request)                         | Request to get OBIS profile.                                                   |
| `0x4c` | [GetObisInfo](./GetObisInfo.md#request)                               | Request to get OBIS information by OBIS ID. Related OBIS and profile..         |
| `0x4e` | [GetObisContent](./GetObisContent.md#request)                         | Request to get OBIS content.                                                   |
| `0x50` | [GetObisContentById](./GetObisContentById.md#request)                 | Request to get OBIS content by OBIS ID.                                        |
| `0x60` | [SetupMeterProfile](./SetupMeterProfile.md#request)                   | Request to setup meter profile.                                                |
| `0x62` | [RemoveMeterProfile](./RemoveMeterProfile.md#request)                 | Request to remove meter profile.                                               |
| `0x64` | [GetMeterProfileIdList](./GetMeterProfileIdList.md#request)           | Get the list of the meter profile id.                                          |
| `0x66` | [GetMeterProfile](./GetMeterProfile.md#request)                       | Request/response to get the meter profile related information                  |
| `0x70` | [SetupMeter](./SetupMeter.md#request)                                 | Request to setup meter. Setup meter id and address...                          |
| `0x72` | [RemoveMeter](./RemoveMeter.md#request)                               | Request to to remove specific meter.                                           |
| `0x74` | [GetMeterIdList](./GetMeterIdList.md#request)                         | Get the list of the meter id.                                                  |
| `0x76` | [GetMeterId](./GetMeterId.md#request)                                 | Request to get the meter id by the meter address.                              |
| `0x78` | [GetMeterInfo](./GetMeterInfo.md#request)                             | Request to get the meter info, like address and meter profile id.              |
| `0x7a` | [GetMeterDate](./GetMeterDate.md#request)                             | Request to get the current date and time on the meter.                         |
| `0x81` | [GetMeterReadoutState](./GetMeterReadoutState.md#request)             | Request to get readout state from the specific meter.                          |


## Uplink commands

| ID     | Name                                                                          | Description                                                                                             |
| ------ | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `0x02` | [GetObserverInfo](./GetObserverInfo.md#request)                               | Response to the [GetObserverInfo](./GetObserverInfo.md#request) downlink command.                       |
| `0x04` | [GetObserverCapabilities](./GetObserverCapabilities.md#response)              | Response to the [GetObserverCapabilities](./GetObserverCapabilities.md#request) downlink command.       |
| `0x06` | [GetObserverUptime](./GetObserverUptime.md#response)                          | Response to the [GetObserverUptime](./GetObserverUptime.md#request) downlink command.                   |
| `0x0a` | [SetSerialPort](./SetSerialPort.md#response)                                  | Response to the [SetSerialPort](./SetSerialPort.md#request) downlink command.                           |
| `0x0c` | [SetSingleMode](./SetSingleMode.md#response)                                  | Response to the [SetSingleMode](./SetSingleMode.md#request) downlink command.                           |
| `0x0e` | [GetSingleMode](./GetSingleMode.md#request)                                   | Response to the [GetSingleMode](./GetSingleMode.md#request) downlink command.                           |
| `0x10` | [GetArchiveState](./GetArchiveState.md#response)                              | Response to the [GetArchiveState](./GetArchiveState.md#request) downlink command.                       |
| `0x12` | [ReadMeterArchive](./ReadMeterArchive.md#response)                            | Response to the [ReadMeterArchive](./ReadMeterArchive.md#request) downlink command.                     |
| `0x14` | [ReadMeterArchiveWithDate](./ReadMeterArchiveWithDate.md#response)            | Response to the [ReadMeterArchiveWithDate](./ReadMeterArchiveWithDate.md#request) downlink command.     |
| `0x21` | [GetLorawanInfo](./GetLorawanInfo.md#response)                                | Response to the [GetLorawanInfo](./GetLorawanInfo.md#request) downlink command.                         |
| `0x23` | [GetLorawanState](./GetLorawanState.md#response)                              | Response to the [GetLorawanState](./GetLorawanState.md#request) downlink command.                       |
| `0x25` | [SetLorawanConnectionMethod](./SetLorawanConnectionMethod.md#response)        | Response to the [SetLorawanConnectionMethod](./SetLorawanConnectionMethod.md#request) downlink command. |
| `0x27` | [Reboot](./Reboot.md#response)                                                | Response to the [Reboot](./Reboot.md#request) downlink command.                                         |
| `0x31` | [UpdateImageWrite](./UpdateImageWrite.md#response)                            | Response to the [UpdateImageWrite](./UpdateImageWrite.md#request) downlink command.                     |
| `0x33` | [UpdateImageVerify](./UpdateImageVerify.md#response)                          | Response to the [UpdateImageVerify](./UpdateImageVerify.md#request) downlink command.                   |
| `0x35` | [UpdateRun](./UpdateRun.md#response)                                          | Response to the [UpdateRun](./UpdateRun.md#request) downlink command.                                   |
| `0x41` | [GetObisIdList](./GetObisIdList.md#response)                                  | Response to the [GetObisIdList](./GetObisIdList.md#request) downlink command.                           |
| `0x43` | [SetupObis](./SetupObis.md#response)                                          | Response to the [SetupObis](./SetupObis.md#request) downlink command.                                   |
| `0x45` | [RemoveObis](./RemoveObis.md#response)                                        | Response to the [RemoveObis](./RemoveObis.md#request) downlink command.                                 |
| `0x47` | [AddObisProfile](./AddObisProfile.md#response)                                | Response to the [AddObisProfile](./AddObisProfile.md#request) downlink command.                         |
| `0x4b` | [GetObisProfile](./GetObisProfile.md#response)                                | Response to the [GetObisProfile](./GetObisProfile.md#request) downlink command.                         |
| `0x4d` | [GetObisInfo](./GetObisInfo.md#response)                                      | Response to the [GetObisInfo](./GetObisInfo.md#request) downlink command.                               |
| `0x4f` | [GetObisContent](./GetObisContent.md#response)                                | Response to the [GetObisContent](./GetObisContent.md#request) downlink command.                         |
| `0x51` | [GetObisContentById](./GetObisContentById.md#response-with-float-content)     | Response to the [GetObisContentById](./GetObisContentById.md#request) downlink command.                 |
| `0x52` | [GetObisContentByIdStr](./GetObisContentById.md#response-with-string-content) | Response to the [GetObisContentByIdStr](./GetObisContentByIdStr.md#request) downlink command.           |
| `0x53` | [ObservationReport](./uplink/ObservationReport.md)                            | Content of the OBIS codes that were captured with float content.                                        |
| `0x54` | [ObservationReportString](./uplink/ObservationReportString.md)                | Content of the OBIS codes that were captured with string content.                                       |
| `0x61` | [SetupMeterProfile](./SetupMeterProfile.md#response)                          | Response to the [SetupMeterProfile](./SetupMeterProfile.md#request) downlink command.                   |
| `0x63` | [RemoveMeterProfile](./RemoveMeterProfile.md#response)                        | Response to the [RemoveMeterProfile](./RemoveMeterProfile.md#request) downlink command.                 |
| `0x65` | [GetMeterProfileIdList](./GetMeterProfileIdList.md#response)                  | Response to the [GetMeterProfileIdList](./GetMeterProfileIdList.md#request) downlink command.           |
| `0x67` | [GetMeterProfile](./GetMeterProfile.md#response)                              | Response to the [GetMeterProfile](./GetMeterProfile.md#request) downlink command.                       |
| `0x71` | [SetupMeter](./SetupMeter.md#response)                                        | Response to the [SetupMeter](./SetupMeter.md#request) downlink command.                                 |
| `0x73` | [RemoveMeter](./RemoveMeter.md#response)                                      | Response to the [RemoveMeter](./RemoveMeter.md#request) downlink command.                               |
| `0x75` | [GetMeterIdList](./GetMeterIdList.md#response)                                | Response to the [GetMeterIdList](./GetMeterIdList.md#request) downlink command.                         |
| `0x77` | [GetMeterId](./GetMeterId.md#response)                                        | Response to the [GetMeterId](./GetMeterId.md#request) downlink command.                                 |
| `0x79` | [GetMeterInfo](./GetMeterInfo.md#response)                                    | Response to the [GetMeterInfo](./GetMeterInfo.md#request) downlink command.                             |
| `0x7b` | [GetMeterDate](./GetMeterDate.md#response)                                    | Response to the [GetMeterDate](./GetMeterDate.md#request) downlink command.                             |
| `0x82` | [GetMeterReadoutState](./GetMeterReadoutState.md#response)                    | Response to the [GetMeterReadoutState](./GetMeterReadoutState.md#request) downlink command.             |
| `0xfe` | [Error](./uplink/Error.md)                                                    | Response to the command with error.                                                                     |


**Note**

All number fields in the commands are transmitted in big-endian format.
