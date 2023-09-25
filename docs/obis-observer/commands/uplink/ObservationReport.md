# ObservationReport

The Observation Report command is used for reporting by the OBIS observer.
The command includes the OBIS content captured according to schedule and contain float values.


### Format

| Size | Type                               | Field                                        |
| ---- | ---------------------------------- | -------------------------------------------- |
| `1`  | `byte`                             | command id = `0x53`                          |
| `1`  | `byte`                             | command size (dynamic, `10+`)                |
| `1`  | [Meter ID](../types.md#meter-id)   | meter unique identifier                      |
| `4`  | [Time 2000](../types.md#time-2000) | date and time at which the data was captured |
| `1`  | [OBIS ID](../types.md#obis-id)     | OBIS ID `1`                                  |
| `4`  | `float32`                          | OBIS content `1`                             |
| ...  | ...                                | ...                                          |
| `1`  | [OBIS ID](../types.md#obis-id)     | OBIS ID `N`                                  |
| `4`  | `float32`                          | OBIS content `N`                             |

### Examples

| Field            | Value                     | Hex          |
| ---------------- | ------------------------- | ------------ |
| command id       | `83`                      | `0x53`       |
| command size     | `15`                      | `0x0f`       |
| meter id         | `2`                       | `0x02`       |
| time             | `2023.12.23 00:00:00 GMT` | `0x2d18df80` |
| OBIS ID `1`      | `50`                      | `0x32`       |
| OBIS content `1` | `34.33`                   | `0x420951ec` |
| OBIS ID `2`      | `56`                      | `0x38`       |
| OBIS content `2` | `45.33`                   | `0x423551ec` |

Message hex dump: `53 0f 02 2d 18 df 80 32 42 09 51 ec 38 42 35 51 ec`


## See also

* [Time 2000](../types.md#time-2000)
* [OBIS ID](../types.md#obis-id)
* [Meter ID](../types.md#meter-id)
