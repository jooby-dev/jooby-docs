# CorrectTimeSmall

Time correction command.
It is used when the time difference is up to `127` seconds.


## Request

### Format

>  Size | Type | Field
> ------|------|-------
>  1    | byte | command id = `0x0c`
>  1    | byte | command size = `2`
>  1    | byte | [sequence number](#sequence-number)
>  1    | byte | [seconds](#seconds)

### Parameters

#### **sequence number**

It's a unique number for each time correction request.
Use the last received [sequence number](./uplink/Time2000.md#sequence-number) + `1` as a starting point.
Then increment this value for each following request.
It should be done to avoid double processing of the request.

#### **seconds**

Amount of seconds to correct device time.
Use positive values to shift time to the future. Negative - to the past.
The new device time will equal the current device time plus the sent value.


### Examples

 Field           | Value  | Dump
-----------------|--------|------
 command id      | `12`   | `0x0c`
 command size    | `2`    | `0x02`
 sequence number | `45`   | `0x2d`
 seconds         | `-120` | `0x88`


## Response

### Format

>  Size | Type | Field
> ------|------|-------
>  1    | byte | command id = `0x0c`
>  1    | byte | length = `1`
>  1    | byte | [status](#status)

### Parameters

#### Status

`1` - the time setting was successful <br>
`0` - time setting failed (the [sequence number](#sequence-number) parameter was not changed)

### Examples

success:

 Field        | Value | Dump
--------------|-------|------
 command id   | `12`  | `0x0c`
 command size | `1`   | `0x01`
 status       | `1`   | `0x01`

failure:

 Field        | Value | Dump
--------------|-------|------
 command id   | `12`  | `0x0c`
 command size | `1`   | `0x01`
 status       | `0`   | `0x00`


## See also

* [Device time management](../basics.md#device-time-management)
* [Downlink command CorrectTime](../commands/CorrectTime.md)
* [Uplink event Time2000](../commands/Time2000.md)
