# Parameter types

Command body structures for [SetParameter](./commands/SetParameter.md).
Attention! Parameter types is not fully documented!


## Reporting data interval

Setting time parameters of operation. Applicable to all types of modules.

### Format

| Size | Type   | Field                              |
| ---- | ------ | ---------------------------------- |
| 1    | `byte` | parameter type = `1`               |
| 3    | `byte` | [reserved](#reserved) = `0x000000` |
| 1    | `byte` | [period](#period)                  |

#### **reserved**

Obsolete parameter. This field is no longer used.

#### **period**

This parameter defines the periodicity of sending data from the sensor.
<br>
It is a `1`-byte value with a resolution of `600` seconds plus a pseudo-random value of up to `511` seconds.
If the parameter is not set, the data transmission period will be `13320` seconds plus a pseudo-random value of up to `2551` seconds.

### Examples

#### set `reporting data interval` to `600` seconds:

| Field          | Value | Hex        |
| -------------- | ----- | ---------- |
| command id     | `3`   | `0x03`     |
| command size   | `5`   | `0x05`     |
| parameter type | `1`   | `0x01`     |
| reserved       |       | `0x000000` |
| period         | `1`   | `0x01`     |

Message hex dump with LRC: `03 05 01 00 00 00 01 53`


## Day checkout hour

The parameter defines the hour of the day by which the daily consumption is calculated.

### Format

| Size | Type   | Field                |
| ---- | ------ | -------------------- |
| 1    | `byte` | parameter type = `4` |
| 1    | `byte` | [hour](#hour)        |

#### **hour**

The value from `0` to `23`. The default calculation hour is `0`.

### Examples

#### set `day checkout hour` to `12:00`:

| Field          | Value | Hex    |
| -------------- | ----- | ------ |
| command id     | `3`   | `0x03` |
| command size   | `2`   | `0x02` |
| parameter type | `4`   | `0x04` |
| hour           | `12`  | `0x0c` |

Message hex dump with LRC: `03 02 04 0c 5c`


## Reporting data type

Parameter of that type used to setup type of values received from device.

### Format

| Size | Type   | Field                   |
| ---- | ------ | ----------------------- |
| 1    | `byte` | parameter type = `5`    |
| 1    | `byte` | [data type](#data-type) |

#### **data type**

| Value | Description  |
| ----- | ------------ |
| `0`   | hour         |
| `1`   | day          |
| `2`   | current      |
| `3`   | hour and day |

### Examples

#### set `reporting data type` to `current`:

| Field          | Value | Hex    |
| -------------- | ----- | ------ |
| command id     | `3`   | `0x03` |
| command size   | `2`   | `0x02` |
| parameter type | `5`   | `0x05` |
| data type      | `2`   | `0x01` |

Message hex dump with LRC: `03 02 05 01 50`


## Priority data delivery type

Data delivery method for priority data.
Can be with acknowledgment or not.
This parameter applies to all types of modules.

### Format

| Size | Type   | Field                           |
| ---- | ------ | ------------------------------- |
| 1    | `byte` | parameter type = `8`            |
| 1    | `byte` | [delivery type](#delivery-type) |

#### **delivery type**

| Value | Description                                    |
| ----- | ---------------------------------------------- |
| `0`   | data with delivery confirmation                |
| `1`   | data transmitted without delivery confirmation |

### Examples

#### set `priority data delivery type` to `data with delivery confirmation`:

| Field          | Value | Hex    |
| -------------- | ----- | ------ |
| command id     | `3`   | `0x03` |
| command size   | `2`   | `0x02` |
| parameter type | `8`   | `0x08` |
| delivery type  | `0`   | `0x00` |

Message hex dump with LRC: `03 02 08 00 5c`


## Activation method

Parameter of that type used to setup activation method in LoRaWAN network.
[Comparison and description of methods](https://www.thethingsindustries.com/docs/devices/abp-vs-otaa/).

### Format

| Size | Type   | Field                                             |
| ---- | ------ | ------------------------------------------------- |
| 1    | `byte` | parameter type = `9`                              |
| 1    | `byte` | [activation method type](#activation-method-type) |

#### **activation method type**

| Value | Description       |
| ----- | ----------------- |
| `0`   | OTAA (by default) |
| `1`   | ABP               |

### Examples

#### set `activation method` to `ABP`:

| Field                  | Value | Hex    |
| ---------------------- | ----- | ------ |
| command id             | `3`   | `0x03` |
| command size           | `2`   | `0x02` |
| parameter type         | `9`   | `0x09` |
| activation method type | `1`   | `0x01` |

Message hex dump with LRC: `03 02 09 01 5c`


## RX2 config

Parameter of that type used to setup `RX2` window configuration

### Format

| Size | Type   | Field                           |
| ---- | ------ | ------------------------------- |
| 1    | `byte` | parameter type = `18`           |
| 1    | `byte` | [spread factor](#spread-factor) |
| 3    | `byte` | [frequency](#frequency)         |

#### **spread factor**

The transmission speed or `Data Rate` of a LoRaWAN message, ranging from `SF7` (highest Data Rate) to `SF12` (lowest Data Rate).
Making the spreading factor `1` step lower (from `SF10` to `SF9`) allows you to roughly send the same amount of data use half the time on air.
Lowering the spreading factor makes it more difficult for the gateway to receive a transmission, as it will be more sensitive to noise.
[More info.](https://www.thethingsnetwork.org/docs/lorawan/spreading-factors/)

| Value | Description |
| ----- | ----------- |
| `0`   | `SF12B125`  |
| `1`   | `SF11B125`  |
| `2`   | `SF10B125`  |
| `3`   | `SF9B125`   |
| `4`   | `SF8B125`   |
| `5`   | `SF7B125`   |
| `6`   | `SF7B250`   |

#### **frequency**

`RX2` data rate frequency.
The second receive window (RX2) uses a fixed frequency and data rate.
This value configures the frequency to use in `RX2`.
Changing the desired value makes the Network Server transmit the RXParamSetupReq MAC command.
<br>
It is a `3`-byte unsigned int BE, real frequency value divided by `100`.

### Examples

#### set spread factor to `SF7B125` and frequency `20000` for RX2 window:

| Field          | Value | Hex        |
| -------------- | ----- | ---------- |
| command id     | `3`   | `0x03`     |
| command size   | `5`   | `0x05`     |
| parameter type | `18`  | `0x12`     |
| spread factor  | `5`   | `0x01`     |
| frequency      | `200` | `0x0000c8` |

Message hex dump with LRC: `03 05 12 05 00 00 c8 8c`


## Absolute data

Parameter of that type used to setup absolute data for not multichannel device

### Format

| Size | Type   | Field                                          |
| ---- | ------ | ---------------------------------------------- |
| 1    | `byte` | parameter type = `23`                          |
| 1    | `byte` | [meter value](#meter-value)                    |
| 3    | `byte` | [pulse coefficient](#pulse-coefficient)        |
| 3    | `byte` | [pulse counter's value](#pulse-counters-value) |

#### **meter value**

Base absolute meter value.
<br>
It is a `4`-byte unsigned int BE.

#### **pulse coefficient**

[Pulse coefficient](./types.md#pulse-coefficient)

#### **pulse counter's value**

Base pulse counter's value.
<br>
It is a `4`-byte unsigned int BE.

### Examples

#### set absolute data (not multichannel device):

| Field                 | Value  | Hex          |
| --------------------- | ------ | ------------ |
| command id            | `3`    | `0x03`       |
| command size          | `10`   | `0x0a`       |
| parameter type        | `23`   | `0x17`       |
| meter value           | `204`  | `0x000000cc` |
| pulse coefficient     | `100`  | `0x83`       |
| pulse counter's value | `2023` | `0x000007e7` |

Message hex dump with LRC: `03 0a 17 00 00 00 cc 83 00 00 07 e7 e4`


## Extra frame interval

`ExtraFrames` handling parameter.

### Format

| Size | Type   | Field                 |
| ---- | ------ | --------------------- |
| 1    | `byte` | parameter type = `28` |
| 2    | `byte` | [interval](#interval) |

#### **interval**

The parameter is `2` bytes long and measured in seconds.
Its value must not be less than `90` seconds.
If the parameter is set to `0`, it means that the issuance of `ExtraFrames` will be prohibited.
GazMoldova modules provide for issuing `ExtraFrame` `UPLINK` frames in case of loss of communication with `NS`.
This will happen after transmitting `16` standard `UPLINK` frames without receiving a confirmation from `NS`.
In `OTAA` connection mode, after more than `5` unsuccessful attempts to connect via `JOINREQ`, the `ExtraFrame` `UPLINK` frame transmission mode will be initiated.

### Examples

#### set `extra frame interval` to `3600` seconds:

| Field          | Value  | Hex      |
| -------------- | ------ | -------- |
| command id     | `3`    | `0x03`   |
| command size   | `3`    | `0x03`   |
| parameter type | `28`   | `0x1c`   |
| interval       | `3600` | `0x100e` |

Message hex dump with LRC: `03 03 1c 10 0e 57`


## Absolute data multi channel

Parameter of that type used to setup absolute data for multichannel device

### Format

| Size | Type   | Field                                          |
| ---- | ------ | ---------------------------------------------- |
| 1    | `byte` | parameter type = `29`                          |
| 1    | `byte` | [channel index](#channel-index)                |
| 1    | `byte` | [meter value](#meter-value)                    |
| 3    | `byte` | [pulse coefficient](#pulse-coefficient)        |
| 3    | `byte` | [pulse counter's value](#pulse-counters-value) |

#### **channel-index**

Channel index number.
<br>
It is a `1`-byte unsigned int.

#### **meter value**

Base absolute meter value.
<br>
It is a `4`-byte unsigned int BE.

#### **pulse coefficient**

[Pulse coefficient](./types.md#pulse-coefficient)

#### **pulse counter's value**

Base pulse counter's value.
<br>
It is a `4`-byte unsigned int BE.

### Examples

#### set absolute data (not multichannel device):

| Field                 | Value  | Hex          |
| --------------------- | ------ | ------------ |
| command id            | `3`    | `0x03`       |
| command size          | `11`   | `0x0b`       |
| parameter type        | `29`   | `0x1d`       |
| channel index number  | `1`    | `0x00`       |
| meter value           | `402`  | `0x00000192` |
| pulse coefficient     | `1000` | `0x84`       |
| pulse counter's value | `2032` | `0x000007f0` |

Message hex dump with LRC: `03 0b 1d 00 00 00 01 92 84 00 00 07 f0 a0`
