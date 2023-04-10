# GetCurrentMul

Command to request\receive current values from device channels.
Periodically sended if [device report data parameter](../parameter-types.md#reporting-data-type) set to
[current](../parameter-types.md#data-type) i.e. = 2.
Time of values - time of receive.

## Request

### Format

>  Size | Type | Field
> ------|------|-------
>  `1`  | byte | command id = `0x18`
>  `1`  | byte | command size = `0`

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

The command has no parameters.

### Examples

 Field        | Value | Dump
--------------|-------|------
 command id   | `24`  | `0x18`
 command size | `0`   | `0x00`


## Response

### Format

>  Size | Type | Field
> ------|------|-------
>  `1`  | byte | command id = `0x18`
>  `1`  | byte | command size = dynamic, 2+ bytes
>  `1+` | byte | [channels](#channels), [extended bit value](../types.md#extended-bit-value)
>  `1+` | byte | [channel value](#channel value), [extended bit value](../types.md#extended-bit-value)

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **channels**

[Extended bit unsigned value](../types.md#extended-bit-value). Maximum 14 channels (16 - 2 EXTENDED bits), size - 2 bytes.
Describe channels which exists in command. Each bit represents one channel.
If bits 0, 1, 2, 3 are set - this means that values from that channels in that order exists in command.

#### **channel value**

[Extended bit value](../types.md#extended-bit-value) unsigned value. Max size 4 bytes.

### Examples


4 channels with values
Command dump: `18 06 0F 83 01 08 0A 0C`

 Field            | Value | Dump
------------------|-------|------
 command id       | `24`  | `0x18`
 command size     | `6`   | `0x06`
 channels         | `15`  | `0x0F`
 channel #0 value | `131` | `0x83 0x01`
 channel #1 value | `8`   | `08`
 channel #2 value | `10`  | `0A`
 channel #3 value | `12`  | `0C`


only channel #1 with value
Command dump: `18 02 01 32`

 Field            | Value | Dump
------------------|-------|------
 command id       | `12`  | `0x18`
 command size     | `2`   | `0x02`
 channels         | `1`   | `0x01`
 channel #1 value | `50`  | `0x32`


## See also

* [Device report data parameter](../parameter-types.md#reporting-data-type)
* [Extended bit value](../types.md#extended-bit-value)
