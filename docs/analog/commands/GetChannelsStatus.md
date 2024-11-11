# GetCurrentMC

Command to get the status of device channels.
If no channels bit set is included in the request, the status for all channels will be returned.

## Request

### Format

| Size   | Type                                         | Field                                            |
| ------ | -------------------------------------------- | ------------------------------------------------ |
| `1`    | `uint8`                                      | extra flag = `0x1f`                              |
| `1`    | `uint8`                                      | command id = `0x32`                              |
| `1`    | `uint8`                                      | command size (dynamic, `0, 1`)                   |
| `1..4` | [extended value](../types.md#extended-value) | [channels bit set](../types.md#channels-bit-set) |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **channels bit set**

[See details](../types.md#channels-bit-set).

### Examples

#### request the status of channels `1` and `2`:

| Field        | Value | Bits         | Hex    |
| ------------ | ----- | ------------ | ------ |
| extra flag   | `31`  |              | `0x1f` |
| command id   | `50`  |              | `0x32` |
| command size | `1`   |              | `0x04` |
| channels     | `1`   | `0b00000011` | `0x03` |

Message hex dump with LRC: `1f 32 01 03 7a`

#### request the status of all channels

| Field        | Value | Bits         | Hex    |
| ------------ | ----- | ------------ | ------ |
| extra flag   | `31`  |              | `0x1f` |
| command id   | `50`  |              | `0x32` |
| command size | `1`   |              | `0x04` |
| channels     | `1`   | `0b00000011` | `0x03` |

Message hex dump with LRC: `1f 32 00 78`


## Response

It's a response to [GetChannelsStatus request](./GetChannelsStatus.md#request).
A response will be sent only if a binary or temperature sensor is assigned to the channel.


| Size | Type    | Field                             |
| ---- | ------- | --------------------------------- |
| `1`  | `uint8` | extra flag = `0x1f`               |
| `1`  | `uint8` | command id = `0x32`               |
| `1`  | `uint8` | command size (dynamic `1+`)       |
| `1`  | `uint8` | channel number                    |
| `1`  | `uint8` | [channel type](#channel-type)     |
| `1+` | `uint8` | [channel status](#channel-status) |

### Parameters

#### **channel type**

One of the [channel type](../parameter-types.md#channel-type-values).

#### **channel status**

##### Idle channel status

For the idle channel no status will be sent.

##### Power channel status

For the power channel no status will be sent.

##### Binary sensor status

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | Binary sensor status. `0` - off, `1` - on |

##### Temperature sensor status

| Size | Type   | Field          |
| ---- | ------ | -------------- |
| `1`  | `int8` | temperature °C |

* [Extended value](../types.md#extended-value)
* [Channels bit set](../types.md#channels-bit-set)
* [Channel types](../parameter-types.md#channel-type-values)
