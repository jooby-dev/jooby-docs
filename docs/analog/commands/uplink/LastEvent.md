# LastEvent

Transmits the sequence number of the last device event and the status bits.

This command will be added to all commands that the device transmits without a request,
except for the [GetStatus](../GetStatus.md) command, since the data is inside the command.
The status bits may differ for different device types.


## Event

### Format

| Size  | Type    | Field                                                                                          |
| ----- | ------- | ---------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id + size = `0x60-0x7f`                                                                |
| `1`   | `uint8` | [sequence number](#sequence-number)                                                            |
| `1-2` | `uint8` | [status](#status) (can be an [extended value](../../types.md#extended-value) for some devices) |

It's a command with a [one-byte header](../../message.md#command-with-a-one-byte-header).<br/>
Max command size is `31` bytes.

### Parameters

#### sequence number

It's the last generated event number.

#### status

Bit set with current device states.
It depends on the device [hardware type](../../basics.md#hardware-types).

##### for `GAS*` devices (`1` byte):

| Bit    | Name     | Description                                                                 |
| ------ | -------- | --------------------------------------------------------------------------- |
| `0`    | `BAT`    | `1` - the battery voltage has dropped below the set threshold               |
| `1`    | `MAGNET` | `1` - there is a magnetic field influence                                   |
| `2`    | `BUTTON` | `0` - button is pressed <br/> `1` - button is release (device is unmounted) |
| `3`    | `DOWN`   | `1` - the device has detected a loss of connection to the server            |
| `4..7` | `RES`    | reserved for future use                                                     |

##### for `IMP2AS`, `IMP2EU`, `IMP2IN`, `NOVATOR` 2-channel devices (`1` byte):

| Bit    | Name   | Description                                                      |
| ------ | ------ | ---------------------------------------------------------------- |
| `0`    | `BAT`  | `1` - the battery voltage has dropped below the set threshold    |
| `1..2` | `RES`  | reserved for future use                                          |
| `3`    | `DOWN` | `1` - the device has detected a loss of connection to the server |
| `4`    | `CHN0` | `1` - the first channel is not active                            |
| `5`    | `CHN1` | `1` - the second channel is not active                           |
| `6..7` | `RES`  | reserved for future use                                          |

##### for `ELIMP` devices (`1` byte):

| Bit    | Name   | Description                                                      |
| ------ | ------ | ---------------------------------------------------------------- |
| `0..2` | `RES`  | reserved for future use                                          |
| `3`    | `DOWN` | `1` - the device has detected a loss of connection to the server |
| `4..7` | `RES`  | reserved for future use                                          |

##### for `IMP4EU`, `IMP4IN` 4-channel devices (`2` extended bytes):

| Byte | Status bits |
| ---- | ----------- |
| `1`  | `7..0`      |
| `2`  | `15..8`     |

| Bit     | Name     | Description                                                      |
| ------- | -------- | ---------------------------------------------------------------- |
| `0`     | `BAT`    | `1` - the battery voltage has dropped below the set threshold    |
| `1..2`  | `RES`    | reserved for future use                                          |
| `3`     | `DOWN`   | `1` - the device has detected a loss of connection to the server |
| `4`     | `CHN0`   | `1` - the first channel is not active                            |
| `5`     | `CHN1`   | `1` - the second channel is not active                           |
| `6`     | `CHN2`   | `1` - the third channel is not active                            |
| `7`     | `EXTEND` | always `1`                                                       |
| `8`     | `CHN3`   | `1` - the forth channel is not active                            |
| `9..14` | `RES`    | reserved for future use                                          |

##### for `MTXLORA` devices (`2` bytes):

| Byte | Status bits |
| ---- | ----------- |
| `1`  | `7..0`      |
| `2`  | `15..8`     |

| Bit      | Description                                      |
| -------- | ------------------------------------------------ |
| `0`      | `1` - meter case is open                         |
| `1`      | `1` - presence of magnetic influence is detected |
| `2`      | `1` - parameters set remotely                    |
| `3`      | `1` - parameters set locally                     |
| `4`      | `1` - meter program restart                      |
| `5`      | `1` - incorrect password and lockout             |
| `6`      | `1` - time set                                   |
| `7`      | `1` - time correction                            |
| `8`      | `1` - meter failure                              |
| `9`      | `1` - meter terminal box is open                 |
| `10`     | `1` - meter module compartment is open           |
| `11`     | `1` - tariff plan changed                        |
| `12`     | `1` - new tariff plan received                   |
| `13..15` | reserved for future use                          |

### Examples

#### for `GAZI3`:

| Field             | Value                             | Hex    |
| ----------------- | --------------------------------- | ------ |
| command id + size | `98`                              | `0x62` |
| sequence number   | `32`                              | `0x20` |
| status            | `0b00001001` <br/> see json below | `0x09` |

```json
{
    "isBatteryLow": true,
    "isButtonReleased": false,
    "isConnectionLost": true,
    "isMagneticInfluence": false
}
```

Message hex dump with LRC: `62 20 09 1e`

#### for `MTXLORA`:

| Field             | Value                                     | Hex      |
| ----------------- | ----------------------------------------- | -------- |
| command id + size | `99`                                      | `0x63`   |
| sequence number   | `48`                                      | `0x30`   |
| status            | `0b1000001100001010` <br/> see json below | `0x830a` |

```json
{
    "isMeterCaseOpen": true,
    "isMagneticInfluence": true,
    "isParametersSetRemotely": false,
    "isParametersSetLocally": false,
    "isMeterProgramRestarted": false,
    "isLockedOut": false,
    "isTimeSet": false,
    "isTimeCorrected": true,
    "isMeterFailure": false,
    "isMeterTerminalBoxOpen": true,
    "isModuleCompartmentOpen": false,
    "isTariffPlanChanged": true,
    "isNewTariffPlanReceived": false
}
```

Message hex dump with LRC: `63 30 83 0a 8f`


## See also

* [Device events](../../basics.md#device-events)
* [Hardware types](../../basics.md#hardware-types)
