# ReadMeterArchive

Request/response to get the meter archive data.


## Request

### Format

| Size | Type                                 | Field                                                   |
| ---- | ------------------------------------ | ------------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x11`                                     |
| `1`  | `uint8`                              | command size                                            |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                      |
| `1`  | `uint8`                              | archive type: <br> `1` - archive 1 <br> `2` - archive 2 |
| `1`  | `uint32_be`                          | index of the first record to get                        |
| `1`  | `uint8`                              | meter unique identifier                                 |


If the index is equal to `0`, the response will include the newest archive content.
The request with the higher index will retrieve the oldest archived content.


### Examples

| Field        | Value       | Hex          |
| ------------ | ----------- | ------------ |
| command id   | `17`        | `0x11`       |
| command size | `7`         | `0x07`       |
| request id   | `33`        | `0x21`       |
| archive type | `Archive 1` | `0x01`       |
| index        | `0`         | `0x00000000` |
| meter id     | `2`         | `0x02`       |

Message hex dump: `11 07 21 01 00 00 00 00 02`


## Response

### Format

| Size | Type                                 | Field                                                                                                                 |
| ---- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x12`                                                                                                   |
| `1`  | `uint8`                              | command size (dynamic, `3+`)                                                                                          |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                                    |
| `1`  | `uint8`                              | is completed flag: <br> `0` - there is more content in the archive <br> `1` - there is no more content in the archive |
| `4`  | [Time 2000](../types.md#time-2000)   | Date `1`. The date and time at which the data was captured                                                            |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                                                                                                           |
| `4`  | `float32`                            | OBIS content `1`                                                                                                      |
| ...  | ...                                  | ...                                                                                                                   |
| `1`  | [OBIS ID](../types.md#obis-od)       | OBIS ID `N`                                                                                                           |
| `4`  | `float32`                            | OBIS content `N`                                                                                                      |
| `1`  | `uint8`                              | Date end flag                                                                                                         |
| `4`  | [Time 2000](../types.md#time-2000)   | Date `2`. The date and time at which the data was captured                                                            |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                                                                                                           |
| `4`  | `float32`                            | OBIS content `1`                                                                                                      |
| ...  | ...                                  | ...                                                                                                                   |
| `1`  | [OBIS ID](../types.md#obis-od)       | OBIS ID `N`                                                                                                           |
| `4`  | `float32`                            | OBIS content `N`                                                                                                      |

#### Date end flag
If a byte with the value 0 immediately follows the OBIS content, it indicates the end-of-date flag. In this case, the subsequent 4 bytes will be interpreted as the next date and time.


### Examples

| Field             | Value                     | Hex          |
| ----------------- | ------------------------- | ------------ |
| command id        | `18`                      | `0x12`       |
| command size      | `31`                      | `0x1f`       |
| request id        | `01`                      | `0x01`       |
| is completed      | `0`                       | `0x00`       |
| date `1`          | `2019.09.24 01:36:00 GMT` | `0x2e7e3c80` |
| OBIS ID `1`       | `8`                       | `0x08`       |
| OBIS content `1`  | `12.00`                   | `0x41400000` |
| date `1` end flag | `0`                       | `0x00`       |
| date `2`          | `2019.09.24 01:34:01 GMT` | `0x2e7e3c09` |
| OBIS ID `1`       | `8`                       | `0x08`       |
| OBIS content `1`  | `12.00`                   | `0x41400000` |
| date `2` end flag | `0`                       | `0x00`       |
| date `3`          | `2019.09.24 01:32:02 GMT` | `0x2e7e3b92` |
| OBIS ID `1`       | `8`                       | `0x08`       |
| OBIS content `1`  | `11.00`                   | `0x41300000` |


Message hex dump: `12 1f 01 00 2e 7e 3c 80 08 41 40 00 00 00 2e 7e 3c 09 08 41 40 00 00 00 2e 7e 3b 92 08 41 30 00 00`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description          |
| ----------- | -------------------- |
| `3`         | Format error.        |
| `9`         | The meter not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Time 2000](../types.md#time-2000)
* [OBIS ID](../types.md#obis-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
