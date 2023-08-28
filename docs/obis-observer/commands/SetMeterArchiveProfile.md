# SetMeterArchiveProfile

Request/response to set the archive settings for the specific meter profile.


## Request

### Format

| Size | Type                                             | Field                                         |
| ---- | ------------------------------------------------ | --------------------------------------------- |
| `1`  | `byte`                                           | command id = `0x68`                           |
| `1`  | `byte`                                           | command size                                  |
| `1`  | [Request ID](../types.md#request-id)             | request/response unique identifier            |
| `1`  | [Meter profile id](../types.md#meter-profile-id) | meter profile unique identifier               |
| `2`  | `uint16_be`                                      | archive period for the `Archive 1` in minutes |
| `2`  | `uint16_be`                                      | archive period for the `Archive 2` in minutes |


### Examples

#### set double default parameters:

| Field            | Value  | Hex      |
| ---------------- | ------ | -------- |
| command id       | `104`  | `0x68`   |
| command size     | `5`    | `0x05`   |
| request id       | `35`   | `0x23`   |
| archive 1 period | `2880` | `0x0b40` |
| archive 2 period | `30`   | `0x001e` |

Message hex dump: `68 05 23 0b 40 00 1e`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x69`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `105` | `0x69` |
| command size | `2`   | `0x02` |
| request id   | `156` | `0x9c` |
| result code  | `0`   | `0x00` |

Message hex dump: `10 9c 00`

#### The meter profile not found:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `105` | `0x69` |
| command size | `2`   | `0x02` |
| request id   | `49`  | `0x31` |
| result code  | `10`  | `0x0a` |

Message hex dump: `69 31 01`


### Result codes:

| Result code | Description                       |
| ----------- | --------------------------------- |
| `0`         | Ok. The Operation was successful. |
| `10`        | The meter profile not found.      |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Meter profile id](../types.md#meter-profile-id)
