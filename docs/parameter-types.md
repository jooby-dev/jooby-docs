# Parameter types

Command body structures for [SetParameters](./commands/SetParameters.md).
Attention! Parameter types is not fully documented!


## Reporting data type

Parameter of that type used to setup type of values received from device.

### Format

> Size | Type | Field
> -----|------|-------
> 1    | byte | type = `5`
> 1    | byte | [data-type](#data-type)

#### **data type**

 Value | Description
-------|-------------
 `0`   | hour
 `1`   | day
 `2`   | current
 `3`   | hour and day

### Examples

[SetParameter](./commands/SetParameters.md) the [reporting data type](#reporting-data-type) to `current`

 Field        | Value | Dump
--------------|-------|------
 command id   | `3`   | `0x03`
 command size | `2`   | `0x02`
 type         | `5`   | `0x05`
 data         | `2`   | `0x01`
