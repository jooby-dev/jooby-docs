# GetObisIdList

Request/response to get the OBIS id list for the specific meter profile.

## Request

### Format

| Size | Type                                             | Mandatory/optional | Field                                                       |
| ---- | ------------------------------------------------ | ------------------ | ----------------------------------------------------------- |
| `1`  | `byte`                                           | mandatory          | command id = `0x40`                                         |
| `1`  | `byte`                                           | mandatory          | command size (dynamic, `2+`)                                |
| `1`  | [Request ID](../types.md#request-id)             | mandatory          | request/response unique identifier                          |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | mandatory          | meter profile unique identifier                             |
| `1`  | `index`                                          | mandatory          | the index of the initial item to start forming the response |


### Examples

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `64`  | `0x40` |
| command size     | `3`   | `0x02` |
| request id       | `3`   | `0x03` |
| meter profile id | `10`  | `0x0a` |
| index            | `0`   | `0x00` |

Message hex dump: `40 03 03 0a 00`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x41`                |
| `1`  | `byte`                               | command size (dynamic, `2+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | is list completed                  |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                        |
| ...  | ...                                  | ...                                |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `N`                        |



### Examples

Response with two OBIS ID

| Field             | Value | Hex    |
| ----------------- | ----- | ------ |
| command id        | `65`  | `0x41` |
| command size      | `4`   | `0x04` |
| request id        | `7`   | `0x07` |
| is list completed | `1`   | `0x01` |
| OBIS ID `1`       | `197` | `0xc5` |
| OBIS ID `2`       | `198` | `0xc6` |

Message hex dump: `41 04 07 01 c5 c6`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                  |
| ----------- | ---------------------------- |
| `3`         | Format error.                |
| `10`        | The meter profile not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS](../types.md#obis)
* [OBIS ID](../types.md#obis-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
