# NewEvent

This frame is formed immediately after an event occurs.

To increase the delivery probability, a frame can be transmitted with an acknowledgement request (at the network layer).
Whether to transmit with a confirmation request or not is determined by the set parameters of the sensor operation.


## Event

### Format

| Size | Type   | Field                               |
| ---- | ------ | ----------------------------------- |
| `1`  | `byte` | command id = `0x15`                 |
| `1`  | `byte` | command size (dynamic, `3+`)        |
| `1`  | `byte` | [event id](#event-id)               |
| `1`  | `byte` | [sequence number](#sequence-number) |
| `1+` | `byte` | [event data](#event-data)           |

It's a command with a [two-bytes header](../../message.md#command-with-a-two-bytes-header).

### Parameters

#### **event id**

One of the [event types](../../basics.md#device-events).

#### **sequence number**

It's the last generated event number.

#### **event data**

Event data specific for the event type.

`MAGNET_ON`, `MAGNET_OFF`, `ACTIVATE`, `DEACTIVATE`, `CAN_OFF`, `INSERT`, `REMOVE`, `COUNTER_OVER`, `OPTOLOW`, `OPTOFLASH`, `JOIN_ACCEPT`

| Size | Type      | Field                                            |
| ---- | --------- | ------------------------------------------------ |
| `4`  | uint32_be | [time 2000](../../types.md#time-2000) in seconds |

`BATTERY_ALARM`

| Size | Type | Field           |
| ---- | ---- | --------------- |
| `2`  | byte | battery voltage |

`ACTIVATE_MTX`

| Size | Type      | Field                                            |
| ---- | --------- | ------------------------------------------------ |
| `4`  | uint32_be | [time 2000](../../types.md#time-2000) in seconds |
| `8`  | byte      | device id (MAC address)                          |

`CONNECT`, `DISCONNECT`

| Size | Type | Field                                                            |
| ---- | ---- | ---------------------------------------------------------------- |
| `1`  | byte | channel number                                                   |
| `1+` | byte | channel value as [extended value](../../types.md#extended-value) |

`EV_MTX`

| Size | Type | Field                                                            |
| ---- | ---- | ---------------------------------------------------------------- |
| `2`  | byte | [status for MTXLORA](./LastEvent.md#for-mtxlora-devices-2-bytes) |

### Examples

#### for `MAGNET_ON`:

| Field           | Value       | Hex          |
| --------------- | ----------- | ------------ |
| command id      | `21`        | `0x15`       |
| command size    | `4`         | `0x04`       |
| event id        | `5`         | `0x05`       |
| sequence number | `2`         | `0x02`       |
| time            | `734015840` | `0x2bc03160` |

Message hex dump with LRC: `15 06 01 02 2b c0 31 60 ff`

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

| Field           | Value | Bits                                                                    | Hex      |
| --------------- | ----- | ----------------------------------------------------------------------- | -------- |
| command id      | `21`  |                                                                         | `0x15`   |
| command size    | `5`   |                                                                         | `0x05`   |
| event id        | `12`  |                                                                         | `0x0c`   |
| sequence number | `2`   |                                                                         | `0x02`   |
| channel number  | `0`   |                                                                         | `0x00`   |
| channel value   | `131` | `0b0000000010000011` <br> with extended bits: <br> `0b0000000110000011` | `0x8301` |

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


## See also

* [Device events](../../basics.md#device-events)
