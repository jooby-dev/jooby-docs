# SetParameters

Parameters setup command. The sensor confirms the execution of the command with [response](#response)


## Request

### Format

> Size | Type | Field
> -----|------|-------
> 1    | byte | command id = `0x03`
> 1    | byte | command dynamic size
> 1    | byte | [parameter type](#parameter-type)
> 1+   | byte | [parameter data](#parameter-data)

### Parameters

#### **parameter type**

See [available parameter types](../parameter-types.md)

#### **parameter data**

Type-specific structures.

### Examples

Set [reporting data type](../parameter-types.md#reporting-data-type) parameter to `day`:

 Field        | Value | Dump
--------------|-------|------
 command id   | `3`   | `0x03`
 command size | `2`   | `0x02`
 type         | `5`   | `0x05`
 data         | `1`   | `0x01`


## Response

It's a mandatory confirmation to [SetParameters request](./SetParameters.md#request).

### Format

> Size | Type | Field
> -----|------|-------
> 1    | byte | command id = `0x03`
> 1    | byte | length = `2`
> 1    | byte | [parameter type](#parameter-type)
> 1    | byte | [status](#status)

### Parameters

#### **parameter type**

See [available parameter types](../parameter-types.md)

#### **status**

`1` - parameter setup was successful <br>
`0` - parameter setting failed, parameter was not changed

### Examples

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
 status       | `0`   | `0x00`
