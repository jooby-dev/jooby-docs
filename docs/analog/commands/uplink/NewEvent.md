# NewEvent

This frame is formed immediately after an event occurs.

To increase the delivery probability, a frame can be transmitted with an acknowledgement request (at the network layer).
Whether to transmit with a confirmation request or not is determined by the set parameters of the sensor operation.


## Event

### Format

| Size | Type    | Field                               |
| ---- | ------- | ----------------------------------- |
| `1`  | `uint8` | command id = `0x15`                 |
| `1`  | `uint8` | command size (dynamic, `3+`)        |
| `1`  | `uint8` | [event id](#event-id)               |
| `1`  | `uint8` | [sequence number](#sequence-number) |
| `1+` | `uint8` | [event data](#event-data)           |

It's a command with a [two-bytes header](../../message.md#command-with-a-two-bytes-header).

### Parameters

#### **event id**

One of the [event types](../../basics.md#device-events).

#### **sequence number**

It's the last generated event number.

#### **event data**

Event data specific for the event type.

The data format for these events `MAGNET_ON`, `MAGNET_OFF`, `ACTIVATE`, `DEACTIVATE`, `CAN_OFF`, `INSERT`, `REMOVE`, `COUNTER_OVER`, `OPTOLOW`, `OPTOFLASH`, `JOIN_ACCEPT`, `BINARY_SENSOR_ON`, `BINARY_SENSOR_OFF`, `TEMPERATURE_SENSOR_HYSTERESIS`, `TEMPERATURE_SENSOR_LOW_TEMPERATURE`, `TEMPERATURE_SENSOR_HIGH_TEMPERATURE` is:

| Size | Type        | Field                                            |
| ---- | ----------- | ------------------------------------------------ |
| `4`  | `uint32_be` | [time 2000](../../types.md#time-2000) in seconds |

`BATTERY_ALARM`

| Size | Type    | Field           |
| ---- | ------- | --------------- |
| `2`  | `uint8` | battery voltage |

`ACTIVATE_MTX`

| Size | Type        | Field                                            |
| ---- | ----------- | ------------------------------------------------ |
| `4`  | `uint32_be` | [time 2000](../../types.md#time-2000) in seconds |
| `8`  | `uint8`     | device id (MAC address)                          |

`CONNECT`, `DISCONNECT`

| Size | Type    | Field                                                            |
| ---- | ------- | ---------------------------------------------------------------- |
| `1`  | `uint8` | channel number                                                   |
| `1+` | `uint8` | channel value as [extended value](../../types.md#extended-value) |

`EV_MTX`

| Size | Type    | Field                                                            |
| ---- | ------- | ---------------------------------------------------------------- |
| `2`  | `uint8` | [status for MTXLORA](./LastEvent.md#for-mtxlora-devices-2-bytes) |

`BINARY_SENSOR_ON`, `BINARY_SENSOR_OFF`

| Size | Type        | Field                                            |
| ---- | ----------- | ------------------------------------------------ |
| `4`  | `uint32_be` | [time 2000](../../types.md#time-2000) in seconds |
| `1`  | `uint8`     | channel number                                   |


`TEMPERATURE_SENSOR_HYSTERESIS`, `TEMPERATURE_SENSOR_LOW_TEMPERATURE`, `TEMPERATURE_SENSOR_HIGH_TEMPERATURE`

| Size | Type        | Field                                            |
| ---- | ----------- | ------------------------------------------------ |
| `4`  | `uint32_be` | [time 2000](../../types.md#time-2000) in seconds |
| `1`  | `uint8`     | channel number                                   |
| `1`  | `int8`      | temperature °C                                   |


### Examples

#### for `MAGNET_ON`:

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `21`        | `0x15`       |
| command size    | `6`         | `0x06`       |
| event id        | `5`         | `0x05`       |
| sequence number | `2`         | `0x02`       |
| time            | `734015840` | `0x2bc03160` |

Message hex dump with LRC: `15 06 05 02 2b c0 31 60 fb`

#### for `BATTERY_ALARM`:

| Field           | Value  | Hex      |
| --------------- | ------ | -------- |
| command id      | `21`   | `0x15`   |
| command size    | `4`    | `0x04`   |
| event id        | `5`    | `0x05`   |
| sequence number | `2`    | `0x02`   |
| battery voltage | `3308` | `0x0cec` |

Message hex dump with LRC: `15 04 05 02 0c ec a3`

#### for `ACTIVATE_MTX`:

| Field           | Value              | Hex                  |
| --------------- | ------------------ | -------------------- |
| command id      | `21`               | `0x15`               |
| command size    | `14`               | `0x0e`               |
| event id        | `11`               | `0x0b`               |
| sequence number | `2`                | `0x02`               |
| time            | `734015840`        | `0x2bc03160`         |
| device id       | `7451974802940758` | `0x001a798817012356` |

Message hex dump with LRC: `15 0e 0b 02 2b c0 31 60 00 1a 79 88 17 01 23 56 75`

#### for `CONNECT`:

| Field           | Value | Bits                                                                      | Hex      |
| --------------- | ----- | ------------------------------------------------------------------------- | -------- |
| command id      | `21`  |                                                                           | `0x15`   |
| command size    | `5`   |                                                                           | `0x05`   |
| event id        | `12`  |                                                                           | `0x0c`   |
| sequence number | `2`   |                                                                           | `0x02`   |
| channel number  | `0`   |                                                                           | `0x00`   |
| channel value   | `131` | `0b0000000010000011` <br/> with extended bits: <br/> `0b0000000110000011` | `0x8301` |

Message hex dump with LRC: `15 05 0c 02 00 83 01 c9`

#### for `EV_MTX`:

| Field           | Value          | Bits                 | Hex      |
| --------------- | -------------- | -------------------- | -------- |
| command id      | `21`           |                      | `0x15`   |
| command size    | `4`            |                      | `0x04`   |
| event id        | `17`           |                      | `0x11`   |
| sequence number | `2`            |                      | `0x02`   |
| status          | see json below | `0b1000001100001010` | `0x830a` |

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

Message hex dump with LRC: `15 04 11 02 83 0a de`

#### for `BINARY_SENSOR_ON`

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `22`        | `0x16`       |
| command size    | `7`         | `0x07`       |
| event id        | `22`        | `0x16`       |
| sequence number | `5`         | `0x05`       |
| time            | `734015840` | `0x2bc03160` |
| channel number  | `1`         | `0x01`       |

Message hex dump with LRC: `15 07 16 05 2b c0 31 60 01 ef`

#### for `BINARY_SENSOR_OFF`

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `23`        | `0x17`       |
| command size    | `7`         | `0x07`       |
| event id        | `23`        | `0x17`       |
| sequence number | `6`         | `0x06`       |
| time            | `734015840` | `0x2bc03160` |
| channel number  | `1`         | `0x01`       |

Message hex dump with LRC: `15 07 17 06 2b c0 31 60 01 ed`

#### for `TEMPERATURE_SENSOR_HYSTERESIS`

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `23`        | `0x17`       |
| command size    | `8`         | `0x08`       |
| event id        | `24`        | `0x18`       |
| sequence number | `7`         | `0x07`       |
| time            | `734015840` | `0x2bc03160` |
| channel number  | `2`         | `0x02`       |
| temperature °C  | `20`        | `0x14`       |

Message hex dump with LRC: `15 08 18 07 2b c0 31 60 02 14 fb`

#### for `TEMPERATURE_SENSOR_LOW_TEMPERATURE`

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `23`        | `0x17`       |
| command size    | `8`         | `0x08`       |
| event id        | `25`        | `0x19`       |
| sequence number | `8`         | `0x08`       |
| time            | `734015840` | `0x2bc03160` |
| channel number  | `2`         | `0x02`       |
| temperature °C  | `3`         | `0x03`       |

Message hex dump with LRC: `15 08 19 08 2b c0 31 60 02 03 e2`

#### for `TEMPERATURE_SENSOR_HIGH_TEMPERATURE`

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `23`        | `0x17`       |
| command size    | `8`         | `0x08`       |
| event id        | `26`        | `0x1a`       |
| sequence number | `9`         | `0x09`       |
| time            | `734015840` | `0x2bc03160` |
| channel number  | `2`         | `0x02`       |
| temperature °C  | `3`         | `0x40`       |

Message hex dump with LRC: `15 08 1a 09 2b c0 31 60 02 28 cb`

## See also

* [Device events](../../basics.md#device-events)
