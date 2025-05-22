# ErrorResponse

Response to provide details for the failed downlink command.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Response

### Format

| Size | Type    | Field                                                            |
| ---- | ------- | ---------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0xfe`                                              |
| `1`  | `uint8` | command size = `2`                                               |
| `1`  | `uint8` | failed command id from the [commands list](./readme.md#commands) |
| `1`  | `uint8` | error code from the table of [result codes](../result-codes.md)  |

### Examples

`ACCESS_DENIED` on [TurnRelayOn](./TurnRelayOn.md) command:

| Field             | Value           | Hex    |
| ----------------- | --------------- | ------ |
| command id        | `254`           | `0xfe` |
| command size      | `2`             | `0x02` |
| failed command id | `24`            | `0x18` |
| error code        | `ACCESS_DENIED` | `0x93` |

Message hex dump: `fe 02 18 93`


## See also

* [Access level](../basics.md#command-access-level)
* [Commands list](./readme.md#commands)
* [Result codes](../result-codes.md)
