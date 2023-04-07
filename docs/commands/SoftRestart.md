# SoftRestart

Command for software restart.

A device restarts in `~30` seconds with new LoRaWAN parameters.


## Request

### Format

>  Size | Type | Field
> ------|------|-------
>  `1`  | byte | command id = `0x19`
>  `1`  | byte | command size = `0`

### Parameters

The command has no parameters.

### Examples

 Field        | Value | Dump
--------------|-------|------
 command id   | `25`  | `0x19`
 command size | `0`   | `0x00`

Message dump with LRC: `19 00 4c`


## Response

It's a mandatory confirmation to [SoftRestart request](./SoftRestart.md#request).

### Format

>  Size | Type | Field
> ------|------|-------
>  `1`  | byte | command id = `0x19`
>  `1`  | byte | length = `0`

### Parameters

The command has no parameters.

### Examples

 Field        | Value | Dump
--------------|-------|------
 command id   | `25`  | `0x19`
 command size | `0`   | `0x00`

Message dump with LRC: `19 00 4c`
