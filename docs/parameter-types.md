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
