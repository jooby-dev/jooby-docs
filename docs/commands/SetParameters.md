# SetParameters

Parameters setup command. The sensor confirms the execution of the command with [response](#response)
Attention! Command is not fully documented!


## Request

### Request format

> Size | Type     | Field
> -----|----------|-------
> 1    | byte     | command id = `0x03`
> 1    | byte     | command dynamic size
> 1    | byte     | [type](#type)
> N    | bytes    | [data](#data)

### Request parameters

#### **type**

Available parameters [types](#types)

> Value | Description
> ------|------------
> 5     | [reporting data type](#reporting-data-type)

#### **data**

Type-specific structures.

### Request examples

Set parameter [reporting data type](#reporting-data-type) to "day"

 Field           | Value    | Dump
-----------------|----------|------
 command id      | `3`      | `0x03`
 command size    | `2`      | `0x02`
 type            | `5`      | `0x05`
 data            | `1`      | `0x01`


## Response

### Response format

> Size | Type | Field
> -----|------|-------
> 1    | byte | command id = `0x03`
> 1    | byte | length = `2`
> 1    | byte | [type](#type)
> 1    | byte | [status](#status)

### Response parameters

#### Status

`1` - parameter setup was successful <br>
`0` - parameter setting failed, parameter was not changed

### Response examples

success:

 Field        | Value | Dump
--------------|-------|------
 command id   | `3`   | `0x03`
 command size | `2`   | `0x02`
 type         | `5`   | `0x05`
 status       | `1`   | `0x01`

failure:

 Field        | Value | Dump
--------------|-------|------
 command id   | `3`   | `0x03`
 command size | `2`   | `0x02`
 type         | `5`   | `0x05`
 status       | `1`   | `0x01`


### Types

#### reporting data type

Type = 5.
Parameter of that type used to setup type of values received from device.
Reporting data type.

Data
Size - **byte**.

> Value | Description
> ------|------------
> 0     | hour
> 1     | day
> 2     | current
> 3     | hour and day
