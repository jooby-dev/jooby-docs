# Result codes

| Code ID | Code Name                                | Description                                                                                                                                |
| ------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `0`     | `OK`                                     |                                                                                                                                            |
| `0x80`  | `UNKNOWN_COMMAND`                        |                                                                                                                                            |
| `0x81`  | `NOT_ALIGNED_DATA`                       |                                                                                                                                            |
| `0x82`  | `DECRYPTION_FAILURE`                     | wrong password                                                                                                                             |
| `0x83`  | `UNKNOWN_PROTOCOL`                       |                                                                                                                                            |
| `0x84`  | `BAD_MESSAGE`                            |                                                                                                                                            |
| `0x85`  | `BAD_DATA_LENGTH`                        |                                                                                                                                            |
| `0x86`  | `BAD_ARRAY_INDEX`                        |                                                                                                                                            |
| `0x87`  | `NOT_PREPARED_RATE_PLAN`                 |                                                                                                                                            |
| `0x88`  | `BAD_RATE_PLAN_ID`                       |                                                                                                                                            |
| `0x89`  | `BAD_RATE_PLAN_SIZE`                     |                                                                                                                                            |
| `0x90`  | `BAD_RESPONSE_LENGTH`                    |                                                                                                                                            |
| `0x91`  | `NO_DATA_FOR_DATE`                       |                                                                                                                                            |
| `0x92`  | `CALIBRATION_DISABLED`                   |                                                                                                                                            |
| `0x93`  | `ACCESS_DENIED`                          |                                                                                                                                            |
| `0x95`  | `BAD_SALDO_WRITE`                        |                                                                                                                                            |
| `0x97`  | `BLOCKED_METER`                          |                                                                                                                                            |
| `0x98`  | `UNENCRYPTED_COMMAND_DISABLED`           |                                                                                                                                            |
| `0x99`  | `TIME_CORRECTION_FAILURE`                | correction more than once per period (`opParams.timeCorrectPeriod`) is forbidden                                                           |
| `0x9a`  | `INVALID_CORRECTION_INTERVAL`            | correction interval (`opParams.deltaCorMin`) exceeded                                                                                      |
| `0x9b`  | `TIME_CORRECTION_OUT_HALF_HOUR_DISABLED` | time correction with crossing the boundary of the current half-hour is prohibited<br/> in case `opParams.timeCorrectPassHalfhour` is false |
| `0x9c`  | `BAD_BLOCK_NUMBER`                       |                                                                                                                                            |
| `0x9f`  | `OUT_OFF_RANGE`                          |                                                                                                                                            |
| `0xa0`  | `SET_METER_TYPE_FAILURE`                 |                                                                                                                                            |
| `0xf0`  | `INTERNAL`                               |                                                                                                                                            |
