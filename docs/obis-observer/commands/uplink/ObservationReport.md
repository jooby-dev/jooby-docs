# ObservationReport

The Observation Report message is used for reporting by the OBIS observer.
The message includes the OBIS content captured according to schedule and contain float values.


### Format

| Size | Type                                 | Field                                        |
| ---- | ------------------------------------ | -------------------------------------------- |
| `1`  | `byte`                               | command id = `0x1a`                          |
| `1`  | `byte`                               | command size (dynamic, `10+`)                |
| `4`  | [Time 2000](../types.md#time-2000)   | date and time at which the data was captured |
| `1`  | [Short name](../types.md#short-name) | short name `1`                               |
| `4`  | `float32`                            | OBIS content `1`                             |
| ...  | ...                                  | ...                                          |
| `1`  | [Short name](../types.md#short-name) | short name `N`                               |
| `4`  | `float32`                            | OBIS content `N`                             |

### Examples

| Field            | Value                     | Hex          |
| ---------------- | ------------------------- | ------------ |
| command id       | `26`                      | `0x1a`       |
| command size     | `14`                      | `0x0e`       |
| time             | `2023.12.23 00:00:00 GMT` | `0x2d18df80` |
| short name `1`   | `50`                      | `0x32`       |
| OBIS content `1` | `34.33`                   | `0x420951ec` |
| short name `2`   | `56`                      | `0x38`       |
| OBIS content `2` | `45.33`                   | `0x423551ec` |

Message hex dump: `1a 0e 2d 18 df 80 32 42 09 51 ec 38 42 35 51 ec`


## See also

* [Time 2000](../types.md#time-2000)
* [Short name](../types.md#short-name)
* [String](../types.md#string)
