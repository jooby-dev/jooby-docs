# SetShortName

Request/response to set short name for the specific OBIS code.


## Request

### Format

| Size  | Type                                 | Field                     |
| ----- | ------------------------------------ | ------------------------- |
| `1`   | `byte`                               | command id = `0x03`       |
| `1`   | `byte`                               | [request id](#request-id) |
| `1`   | [short name](../types.md#short-name) | short name                |
| `3-7` | [OBIS](../types.md#obis)             | OBIS code                 |

### Parameters

#### **request id**

It's a unique number to link request with response.
It should be incremented for each request.
It should be done to avoid double processing of the request.

### Examples

#### set short name `44` for OBIS `0.9.1`

| Field      | Value | Hex          |
| ---------- | ----- | ------------ |
| command id | `3`   | `0x03`       |
| request id | `4`   | `0x04`       |
| short name | `44`  | `0x2c`       |
| obis       |       | `0x02000901` |

Message hex dump: `03 04 2c 02 00 09 01`


## Response

### Format

| Size  | Type   | Field                       |
| ----- | ------ | --------------------------- |
| `1`   | `byte` | command id = `0x04`         |
| `1`   | `byte` | [request id](#request-id)   |
| `1`   | `byte` | [result code](#result-code) |

### Parameters

#### **request id**

It's a unique number to link request with response.

#### **result code**

Operation result
<br>
One of the [result codes](../types.md#result-code).

### Examples

#### success setup:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `04`  | `0x04` |
| request id  | `04`  | `0x04` |
| result code | `0`   | `0x00` |

Message hex dump: `04 04 00`


## See also

* [OBIS code](../types.md#obis)
* [Short name](../types.md#short-name)
* [Result code](../types.md#result-code)
