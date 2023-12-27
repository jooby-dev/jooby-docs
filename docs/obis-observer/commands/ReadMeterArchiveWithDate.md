# ReadMeterArchiveWithDate

Request/response to get the meter archive data for the specific date.

## Request

### Format

| Size | Type                                 | Field                                                   |
| ---- | ------------------------------------ | ------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x13`                                     |
| `1`  | `byte`                               | command size                                            |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                      |
| `1`  | `byte`                               | archive type: <br> `1` - archive 1 <br> `2` - archive 2 |
| `1`  | `uint32_be`                          | index of the first record to get                        |
| `1`  | `byte`                               | meter unique identifier                                 |
| `4`  | [Time 2000](../types.md#time-2000)   | The date of the archive records to read                 |


If the index is equal to `0`, the response will include the newest archive content.
The request with the higher index will retrieve the oldest archived content.


### Examples

| Field        | Value                     | Hex          |
| ------------ | ------------------------- | ------------ |
| command id   | `19`                      | `0x13`       |
| command size | `11`                      | `0x0b`       |
| request id   | `13`                      | `0x0d`       |
| archive type | `Archive 2`               | `0x02`       |
| index        | `0`                       | `0x00000000` |
| meter id     | `1`                       | `0x01`       |
| date         | `2023.09.23 00:00:02 GMT` | `0x2ca0e702` |

Message hex dump: `13 0b 0d 02 00 00 00 00 01 2c a0 e7 02`


## Response

| Size | Type                                 | Field                                                                                                                 |
| ---- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x11`                                                                                                   |
| `1`  | `byte`                               | command size (dynamic, `2+`)                                                                                          |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                                    |
| `1`  | `byte`                               | is completed flag: <br> `0` - there is more content in the archive <br> `1` - there is no more content in the archive |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                                                                                                           |
| `4`  | `float32`                            | OBIS content `1`                                                                                                      |
| ...  | ...                                  | ...                                                                                                                   |
| `1`  | [OBIS ID](../types.md#obis-od)       | OBIS ID `N`                                                                                                           |
| `4`  | `float32`                            | OBIS content `N`                                                                                                      |

#### Date end flag
If a byte with the value 0 immediately follows the OBIS content, it indicates the end-of-date flag. In this case, the subsequent 4 bytes will be interpreted as the next date and time.


### Examples

| Field            | Value  | Hex          |
| ---------------- | ------ | ------------ |
| command id       | `20`   | `0x14`       |
| command size     | `7`    | `0x07`       |
| request id       | `13`   | `0x0d`       |
| is completed     | `1`    | `0x01`       |
| OBIS ID `1`      | `8`    | `0x08`       |
| OBIS content `1` | `3.85` | `0x407624dd` |

Message hex dump: `14 07 0d 01 08 40 76 24 dd`

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
