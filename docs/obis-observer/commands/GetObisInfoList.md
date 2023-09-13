# GetObisIdList

Request/response to get the OBIS ID list for the specific OBIS code and meter profile.


## Request

### Format

| Size | Type                                             | Mandatory/optional | Field                                                       |
| ---- | ------------------------------------------------ | ------------------ | ----------------------------------------------------------- |
| `1`  | `byte`                                           | mandatory          | command id = `0x42`                                         |
| `1`  | `byte`                                           | mandatory          | command size (dynamic, `2+`)                                |
| `1`  | [Request ID](../types.md#request-id)             | mandatory          | request/response unique identifier                          |
| `1`  | [Meter profile ID](../types.md#meter-profile-id) | mandatory          | meter profile unique identifier                             |
| `1`  | `index`                                          | mandatory          | the index of the initial item to start forming the response |


### Examples

| Field            | Value | Hex    |
| ---------------- | ----- | ------ |
| command id       | `66`  | `0x42` |
| command size     | `3`   | `0x02` |
| request id       | `3`   | `0x03` |
| meter profile id | `10`  | `0x0a` |
| index            | `0`   | `0x00` |

Message hex dump: `42 03 03 0a 00`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x43`                |
| `1`  | `byte`                               | command size (dynamic, `2+`)       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | is list completed                  |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                        |
| `1`  | [OBIS info flags](#obis-info-flags)  | OBIS info flag for the OBIS ID `1` |
| ...  | ...                                  | ...                                |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `N`                        |
| `1`  | [OBIS info flags](#obis-info-flags)  | OBIS info flag for the OBIS ID `N` |


#### OBIS info flags

| Bit 7 - Bit 2 | Bit 1                                                                            | Bit 0                                                                         |
| ------------- | -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| reserved      | `0` - not linked to the OBIS profile, <br> `1` - has the linked the OBIS profile | `0` - that is the reassignable OBIS id, <br> `1` - that is the static OBIS id |



### Examples

Response with two OBIS ID
-  OBIS ID 197, static, linked to the OBIS profile
-  OBIS ID 198, static, not linked to the OBIS profile

| Field             | Value | Hex    |
| ----------------- | ----- | ------ |
| command id        | `67`  | `0x43` |
| command size      | `6`   | `0x06` |
| request id        | `7`   | `0x07` |
| is list completed | `1`   | `0x01` |
| OBIS ID `1`       | `197` | `0xc5` |
| OBIS ID flag      | `3`   | `0x03` |
| OBIS ID `2`       | `198` | `0xc6` |
| OBIS ID flag      | `1`   | `0x01` |


## See also

* [Request ID](../types.md#request-id)
* [Meter profile ID](../types.md#meter-profile-id)
* [OBIS](../types.md#obis)
* [OBIS ID](../types.md#obis-id)
