# Commands

There are `2` types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)

| ID     | Name                 | Access level     | Links                                                                                     | Description                                                                                            |
| ------ | -------------------- | ---------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `0x04` | `GetDeviceType`      | `READ_ONLY`      | [request](./GetDeviceType.md#request) / [response](./GetDeviceType.md#response)           | Get the device type.                                                                                   |
| `0x05` | `GetDeviceId`        | `READ_ONLY`      | [request](./GetDeviceId.md#request) / [response](./GetDeviceId.md#response)               | Get the device identifier.                                                                             |
| `0x06` | `RunTariffPlan`      | **`READ_WRITE`** | [request](./RunTariffPlan.md#request) / [response](./RunTariffPlan.md#response)           | Instant activation of the passive tariff plan.                                                         |
| `0x07` | `GetDateTime`        | `READ_ONLY`      | [request](./GetDateTime.md#request) / [response](./GetDateTime.md#response)               | Get the device full date and time with [DST](https://en.wikipedia.org/wiki/Daylight_saving_time) flag. |
| `0x08` | `SetDateTime`        | `READ_ONLY`      | [request](./SetDateTime.md#request) / [response](./SetDateTime.md#response)               | Set the device full date and time with [DST](https://en.wikipedia.org/wiki/Daylight_saving_time) flag. |
| `0x09` | `SetAccessKey`       | **`READ_WRITE`** | [request](./SetAccessKey.md#request) / [response](./SetAccessKey.md#response)             | Set the device access key.                                                                             |
| `0x0d` | `GetCurrentValues`   | `READ_ONLY`      | [request](./GetCurrentValues.md#request) / [response](./GetCurrentValues.md#response)     | Get current values like voltage, power, etc.                                                           |
| `0x0f` | `GetEnergyCurrent`   | `READ_ONLY`      | [request](./GetEnergyCurrent.md#request) / [response](./GetEnergyCurrent.md#response)     | Get current energy A+ by default or selected energy type for 4 tariffs (T1-T4).                        |
| `0x13` | `ActivateRatePlan`   | **`READ_WRITE`** | [request](./ActivateRatePlan.md#request) / [response](./ActivateRatePlan.md#response)     | Provide the date and parameters of tariff plan activation.                                             |
| `0x14` | `PrepareRatePlan`    | **`READ_WRITE`** | [request](./PrepareRatePlan.md#request) / [response](./PrepareRatePlan.md#response)       | Prepare device for rate plan application.                                                              |
| `0x18` | `TurnRelayOn`        | **`READ_WRITE`** | [request](./TurnRelayOn.md#request) / [response](./TurnRelayOn.md#response)               | Turn the device relay on.                                                                              |
| `0x19` | `TurnRelayOff`       | **`READ_WRITE`** | [request](./TurnRelayOff.md#request) / [response](./TurnRelayOff.md#response)             | Turn the device relay off.                                                                             |
| `0x1c` | `SetCorrectTime`     | **`READ_WRITE`** | [request](./SetCorrectTime.md#request) / [response](./SetCorrectTime.md#response)         | Set [DST](https://en.wikipedia.org/wiki/Daylight_saving_time)/Standard time transition options.        |
| `0x28` | `GetVersion`         | `READ_ONLY`      | [request](./GetVersion.md#request) / [response](./GetVersion.md#response)                 | Get device version information.                                                                        |
| `0x29` | `GetSaldo`           | `READ_ONLY`      | [request](./GetSaldo.md#request) / [response](./GetSaldo.md#response)                     | Get device current saldo information.                                                                  |
| `0x2a` | `SetSaldo`           | **`READ_WRITE`** | [request](./SetSaldo.md#request) / [response](./SetSaldo.md#response)                     | Set device current saldo information.                                                                  |
| `0x2c` | `GetRatePlanInfo`    | `READ_ONLY`      | [request](./GetRatePlanInfo.md#request) / [response](./GetRatePlanInfo.md#response)       | Get device rate plan information.                                                                      |
| `0x2e` | `GetSaldoParameters` | `READ_ONLY`      | [request](./GetSaldoParameters.md#request) / [response](./GetSaldoParameters.md#response) | Get device current saldo parameters information.                                                       |
| `0x2f` | `SetSaldoParameters` | **`READ_WRITE`** | [request](./SetSaldoParameters.md#request) / [response](./SetSaldoParameters.md#response) | Set device current saldo parameters information.                                                       |
| `0x3b` | `GetDayProfile`      | `READ_ONLY`      | [request](./GetDayProfile.md#request) / [response](./GetDayProfile.md#response)           | Get day profile information for the given tariff table.                                                |
| `0x3e` | `GetCorrectTime`     | `READ_ONLY`      | [request](./GetCorrectTime.md#request) / [response](./GetCorrectTime.md#response)         | Get [DST](https://en.wikipedia.org/wiki/Daylight_saving_time)/Standard time transition options.        |
| `0x5c` | `SetCorrectDateTime` | `READ_ONLY`      | [request](./SetCorrectDateTime.md#request) / [response](./SetCorrectDateTime.md#response) | Incremental device time correction (for a given number of seconds).                                    |
| `0x5d` | `SetDisplayParam`    | **`READ_WRITE`** | [request](./SetDisplayParam.md#request) / [response](./SetDisplayParam.md#response)       | Set the meter displays sorting order.                                                                  |
| `0x5e` | `GetDisplayParam`    | `READ_ONLY`      | [request](./GetDisplayParam.md#request) / [response](./GetDisplayParam.md#response)       | Get the meter displays sorting order.                                                                  |
| `0x70` | `GetBuildVersion`    | `READ_ONLY`      | [request](./GetBuildVersion.md#request) / [response](./GetBuildVersion.md#response)       | Get firmware build date and version from device.                                                       |
| `0x78` | `GetDayEnergies`     | `UNENCRYPTED`    | [event](./uplink/GetDayEnergies.md)                                                       | Event to get day energies by 4 tariffs (T1-T4). Can be transmitted only via Lora.                      |
| `0xfe` | `ErrorResponse`      | `READ_ONLY`      | [response](./ErrorResponse.md#response)                                                   | Provide info for the failed downlink command.                                                          |


**Note**

All number fields in the commands are transmitted in big-endian format.
