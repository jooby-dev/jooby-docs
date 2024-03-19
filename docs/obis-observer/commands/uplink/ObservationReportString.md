# ObservationReportString

The Observation Report String command is used for reporting by the OBIS observer.
The command includes the OBIS content captured according to schedule and contain string values.


### Format

| Size | Type                               | Field                                        |
| ---- | ---------------------------------- | -------------------------------------------- |
| `1`  | `uint8`                            | command id = `0x54`                          |
| `1`  | `uint8`                            | command size (dynamic, `10+`)                |
| `4`  | [Meter ID](../types.md#meter-id)   | meter unique identifier                      |
| `4`  | [Time 2000](../types.md#time-2000) | date and time at which the data was captured |
| `1`  | [OBIS ID](../types.md#obis-id)     | OBIS ID `1`                                  |
| `4`  | [String](../types.md#string)       | OBIS content `1`                             |
| ...  | ...                                | ...                                          |
| `1`  | [OBIS ID](../types.md#obis-id)     | OBIS ID `N`                                  |
| `4`  | [String](../types.md#string)       | OBIS content `N`                             |

### Examples

| Field            | Value                        | Hex                                                        |
| ---------------- | ---------------------------- | ---------------------------------------------------------- |
| command id       | `84`                         | `0x54`                                                     |
| command size     | `62`                         | `0x3e`                                                     |
| meter id         | `2`                          | `0x00000002`                                               |
| time             | `2023.12.23 00:00:00 GMT`    | `0x2d18df80`                                               |
| OBIS ID `1`      | `50`                         | `0x32`                                                     |
| OBIS content `1` | `reactive power QI, average` | `0x1a726561637469766520706f7765722051492c2061766572616765` |
| OBIS ID `2`      | `56`                         | `0x38`                                                     |
| OBIS content `2` | `reactive power QI, total`   | `0x18726561637469766520706f7765722051492c20746f74616c`     |

Message hex dump: `54 3e 00 00 00 02 2d 18 df 80 32 1a 72 65 61 63 74 69 76 65 20 70 6f 77 65 72 20 51 49 2c 20 61 76 65 72 61 67 65 38 18 72 65 61 63 74 69 76 65 20 70 6f 77 65 72 20 51 49 2c 20 74 6f 74 61 6c`


## See also

* [Time 2000](../types.md#time-2000)
* [OBIS ID](../types.md#obis-id)
* [String](../types.md#string)
* [Meter ID](../types.md#meter-id)
