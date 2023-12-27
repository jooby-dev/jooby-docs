# ReadArchive

Request/response to get the meter archive data.


## Request

### Format

| Size | Type                                 | Field                                                   |
| ---- | ------------------------------------ | ------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x15`                                     |
| `1`  | `byte`                               | command size                                            |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                      |
| `1`  | `byte`                               | archive type: <br> `1` - archive 1 <br> `2` - archive 2 |
| `1`  | `uint32_be`                          | index of the first record to get                        |


If the index is equal to `0`, the response will include the newest archive content.
The request with the higher index will retrieve the oldest archived content.


### Examples

| Field        | Value       | Hex          |
| ------------ | ----------- | ------------ |
| command id   | `21`        | `0x15`       |
| command size | `7`         | `0x07`       |
| request id   | `33`        | `0x21`       |
| archive type | `Archive 1` | `0x01`       |
| index        | `0`         | `0x00000000` |

Message hex dump: `15 06 21 01 00 00 00 00`


## Response

### Format

| Size | Type                                 | Field                                                                                                                 |
| ---- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x16`                                                                                                   |
| `1`  | `byte`                               | command size (dynamic, `3+`)                                                                                          |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                                    |
| `1`  | `byte`                               | is completed flag: <br> `0` - there is more content in the archive <br> `1` - there is no more content in the archive |
| `4`  | [Meter ID](../types.md#meter-id)     | meter unique identifier `1`                                                                                           |
| `4`  | [Time 2000](../types.md#time-2000)   | date `1`. The date and time at which the data was captured                                                            |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                                                                                                           |
| `4`  | `float32`                            | OBIS content `1`                                                                                                      |
| ...  | ...                                  | ...                                                                                                                   |
| `1`  | [OBIS ID](../types.md#obis-od)       | OBIS ID `N`                                                                                                           |
| `4`  | `float32`                            | OBIS content `N`                                                                                                      |
| `1`  | `byte`                               | meter end flag                                                                                                        |
| `4`  | [Meter ID](../types.md#meter-id)     | meter unique identifier `2`                                                                                           |
| `4`  | [Time 2000](../types.md#time-2000)   | date `2`. The date and time at which the data was captured                                                            |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                                                                                                           |
| `4`  | `float32`                            | OBIS content `1`                                                                                                      |
| ...  | ...                                  | ...                                                                                                                   |
| `1`  | [OBIS ID](../types.md#obis-od)       | OBIS ID `N`                                                                                                           |
| `4`  | `float32`                            | OBIS content `N`                                                                                                      |

#### Date end flag
If a byte with the value 0 immediately follows the OBIS content, it indicates the end-of-date flag. In this case, the subsequent 4 bytes will be interpreted as the next date and time.


### Examples

| Field              | Value                     | Hex          |
| ------------------ | ------------------------- | ------------ |
| command id         | `22`                      | `0x16`       |
| command size       | `34`                      | `0x22`       |
| request id         | `01`                      | `0x09`       |
| is completed       | `1`                       | `0x01`       |
| meter id `1`       | `1`                       | `0x00000001` |
| date `1`           | `2023.10.10 20:26:16 GMT` | `0x14560168` |
| OBIS ID `1`        | `108`                     | `0x6c`       |
| OBIS content `1`   | `0.20`                    | `0x3e4ccccd` |
| meter `1` end flag | `0`                       | `0x00`       |
| meter id `2`       | `2`                       | `0x00000002` |
| date `2`           | `2023.10.10 20:26:15 GMT` | `0x14560167` |
| OBIS ID `1`        | `8`                       | `0x08`       |
| OBIS content `1`   | `0.20`                    | `0x3e4ccccd` |
| OBIS ID `2`        | `108`                     | `0x6c`       |
| OBIS content `2`   | `0.20`                    | `0x3e4ccccd` |


Message hex dump: `16 22 09 01 00 00 00 01 14 56 01 68 6c 3e 4c cc cd 00 00 00 00 02 14 56 01 67 08 3e 4c cc cd 6c 3e 4c cc cd`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description   |
| ----------- | ------------- |
| `3`         | Format error. |

## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Time 2000](../types.md#time-2000)
* [OBIS ID](../types.md#obis-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
