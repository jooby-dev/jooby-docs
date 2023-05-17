# GetShortName

Request/response the short name list of the specific OBIS code.


## Request

### Format

| Size  | Type   | Field                     |
| ----- | ------ | ------------------------- |
| `1`   | `byte` | command id = `0x01`       |
| `1`   | `byte` | [request id](#request-id) |
| `3-7` | `byte` | [obis](#obis)             |

### Parameters

#### **request id**

It's a unique number to link request with response.
It should be incremented for each request.
It should be done to avoid double processing of the request.

#### **obis**

Obis code.
<br>
[See details](../types.md#obis).

### Examples

#### get short name for OBIS `0.9.1`

| Field      | Value | Hex          |
| ---------- | ----- | ------------ |
| command id | `1`   | `0x01`       |
| request id | `2`   | `0x03`       |
| obis       |       | `0x02000901` |

Message hex dump: `01 03 02 00 09 01`


## Response

### Format

| Size  | Type   | Field                        |
| ----- | ------ | ---------------------------- |
| `1`   | `byte` | command id = `0x02`          |
| `1`   | `byte` | command size (dynamic, `4+`) |
| `1`   | `byte` | [request id](#request-id)    |
| `3-7` | `byte` | [obis](#obis)                |
| `1`   | `byte` | short name `1`               |
| ...   | ...    | ...                          |
| `1`   | `byte` | short name `N`               |

### Parameters

#### **request id**

It's a unique number to link request with response.

#### **obis**

Obis code.
<br>
[See details](../types.md#obis).

### Examples

#### short name list for OBIS `0.9.1`:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `12`  | `0x0c` |
| command size | `1`   | `0x01` |
| status       | `1`   | `0x01` |

Message hex dump with LRC: `0c 01 01 59`

#### failure:

| Field          | Value | Hex          |
| -------------- | ----- | ------------ |
| command id     | `2`   | `0x02`       |
| command size   | `7`   | `0x07`       |
| request id     | `3`   | `0x03`       |
| obis           |       | `0x02000901` |
| short name `1` | `197` | `0xc5`       |
| short name `2` | `198` | `0xc6`       |

Message hex dump with: `02 07 03 02 00 09 01 c5 c6`


## See also

* [OBIS code](../types.md#obis)
