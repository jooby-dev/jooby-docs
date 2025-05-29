# GetCriticalEvent

Request/response to get device critical events.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                  |
| ---- | ------- | ------------------------------------------------------ |
| `1`  | `uint8` | command id = `0x56`                                    |
| `1`  | `uint8` | command size = `2`                                     |
| `1`  | `uint8` | [event type](#event-type)                              |
| `1`  | `uint8` | event offset (`0..7`, `255` - the last critical event) |

### Parameters

#### **event type**

One of the following event types:

| ID   | Name                                                                                |
| ---- | ----------------------------------------------------------------------------------- |
| `0`  | meter enclosure opened                                                              |
| `1`  | electromagnetic interference detected                                               |
| `2`  | remote parameter configuration                                                      |
| `3`  | local parameter configuration                                                       |
| `4`  | meter firmware restart                                                              |
| `5`  | incorrect password and lockout                                                      |
| `6`  | time set                                                                            |
| `7`  | time correction                                                                     |
| `8`  | meter failure                                                                       |
| `9`  | meter terminal box opened                                                           |
| `10` | meter module compartment opened                                                     |
| `11` | tariff plan changed                                                                 |
| `12` | new tariff plan received                                                            |
| `13` | electromagnetic interference message reset (on display) (`302.37.001`) `302.35.005` |
| `14` | magnetic interference message reset (on display) (`302.37.001`) `302.35.005`        |


### Examples

| Field        | Value                              | Hex    |
| ------------ | ---------------------------------- | ------ |
| command id   | `86`                               | `0x56` |
| command size | `2`                                | `0x02` |
| event type   | electromagnetic influence detected | `0x01` |
| event offset | `2`                                | `0x02` |

Command hex dump: `56 02 01 02`


## Response

### Format

| Size | Type    | Field                                                          |
| ---- | ------- | -------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x56`                                            |
| `1`  | `uint8` | command size = `9`                                             |
| `1`  | `uint8` | [event type](#event-type)                                      |
| `1`  | `uint8` | event offset (`0..7`, `255` - the last critical event)         |
| `1`  | `uint8` | date of the last critical event (number of years after `2000`) |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                      |
| `1`  | `uint8` | date (month day number which starts from `1`)                  |
| `1`  | `uint8` | hours                                                          |
| `1`  | `uint8` | minutes                                                        |
| `1`  | `uint8` | seconds                                                        |
| `1`  | `uint8` | number of events for a given date                              |

### Examples

Default parameters:

| Field            | Value                              | Hex    |
| ---------------- | ---------------------------------- | ------ |
| command id       | `86`                               | `0x56` |
| command size     | `9`                                | `0x09` |
| event type       | electromagnetic influence detected | `0x01` |
| event offset     | `1`                                | `0x01` |
| year             | `23`                               | `0x17` |
| month            | `3` (March)                        | `0x03` |
| date             | `12`                               | `0x0c` |
| hours            | `10`                               | `0x0a` |
| minutes          | `22`                               | `0x16` |
| seconds          | `33`                               | `0x21` |
| number of events | `7`                                | `0x07` |

Command hex dump: `56 09 01 01 17 03 0c 0a 16 21 07`


## See also

* [Access level](../basics.md#command-access-level)
