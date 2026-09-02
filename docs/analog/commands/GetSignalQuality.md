# GetSignalQuality

NB-IoT signal quality.

Used as a response to this downlink command or as an additional command on each uplink message if parameter `0x39` is enabled.


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | extra flag = `0x1f` |
| `1`  | `uint8` | command id = `0x34` |
| `1`  | `uint8` | command size = `0`  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `52`  | `0x34` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 34 00 7e`


## Response

### Format

| Size | Type    | Field                         |
| ---- | ------- | ----------------------------- |
| `1`  | `uint8` | extra flag = `0x1f`           |
| `1`  | `uint8` | command id = `0x34`           |
| `1`  | `uint8` | command size = `6`            |
| `1`  | `int8`  | [RSSI](#rssi) in `dBm`        |
| `1`  | `int8`  | [RSRP](#rsrp) in `dBm`        |
| `1`  | `int8`  | [RSRQ](#rsrq) in `dB`         |
| `1`  | `int8`  | [SINR](#sinr) in `dB`         |
| `1`  | `int8`  | [Tx power](#tx-power) in `dBm` |
| `1`  | `uint8` | [ECL](#ecl)                   |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### RSSI

Received Signal Strength Indicator. Total received power, including interference, in `dBm`.

#### RSRP

Reference Signal Received Power. Average power of the serving-cell reference signal, in `dBm`.

#### RSRQ

Reference Signal Received Quality. Ratio of RSRP to total received power, in `dB`.

#### SINR

Signal-to-Interference-plus-Noise Ratio, in `dB`.

#### Tx power

Device transmit power, in `dBm`.

#### ECL

Coverage enhancement level:

| Value | Description            |
| ----- | ---------------------- |
| `0`   | Normal coverage        |
| `1`   | Extended coverage      |
| `2`   | Ultra-extended coverage |

### Examples

| Field        | Value  | Hex    |
| ------------ | ------ | ------ |
| extra flag   | `31`   | `0x1f` |
| command id   | `52`   | `0x34` |
| command size | `6`    | `0x06` |
| RSSI         | `-73`  | `0xb7` |
| RSRP         | `-77`  | `0xb3` |
| RSRQ         | `-4`   | `0xfc` |
| SINR         | `18`   | `0x12` |
| Tx power     | `1`    | `0x01` |
| ECL          | `0`    | `0x00` |

Message hex dump with LRC: `1f 34 06 b7 b3 fc 12 01 00 93`
