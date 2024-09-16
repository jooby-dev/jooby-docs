# SetSaldoParameters

Request/response to set device current saldo parameters information.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                  |
| ---- | -------- | ---------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x2f`                                                    |
| `1`  | `uint8`  | command size = `37`                                                    |
| `4`  | `uint32` | saldo coefficients for tariffs `T1`-`T4`                               |
| `1`  | `uint8`  | decimal point in the saldo coefficient for the tariff (default is `4`) |
| `4`  | `int32`  | threshold at which the saldo is indicated                              |
| `1`  | `int32`  | threshold at which relay turns off based on saldo                      |
| `1`  | `uint8`  | definitions setting the operating mode based on saldo                  |
| `1`  | `uint8`  | not to deactivate based on saldo after                                 |
| `1`  | `uint8`  | not to deactivate based on saldo before                                |
| `1`  | `uint8`  | decimal point for saldo indication                                     |
| `1`  | `uint32` | power limitation based on saldo                                        |
| `1`  | `int32`  | saldo credit limit                                                     |

### Examples

| Field                    | Value              | Hex                                  |
| ------------------------ | ------------------ | ------------------------------------ |
| command id               | `47`               | `0x2f`                               |
| command size             | `37`               | `0x25`                               |
| coefficients             | `2`, `3`, `4`, `5` | `0x00000002000000030000000400000005` |
| decimal point            | `6`                | `0x06`                               |
| indication threshold     | `7`                | `0x00000007`                         |
| relay threshold          | `8`                | `0x00000008`                         |
| mode                     | `9`                | `0x09`                               |
| on saldo after           | `10`               | `0x0a`                               |
| on saldo before          | `11`               | `0x0b`                               |
| decimal point indication | `12`               | `0x0c`                               |
| power threshold          | `13`               | `0x0000000d`                         |
| credit threshold         | `14`               | `0x0000000e`                         |

Message hex dump: `2f 25 00 00 00 02 00 00 00 03 00 00 00 04 00 00 00 05 06 00 00 00 07 00 00 00 08 09 0a 0b 0c 00 00 00 0d 00 00 00 0e`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x2f` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `47`  | `0x2f` |
| command size | `0`   | `0x00` |

Message hex dump: `2f 00`


## See also

* [Access level](../basics.md#command-access-level)
