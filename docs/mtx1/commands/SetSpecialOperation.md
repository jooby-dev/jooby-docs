# SetSpecialOperation

Request/response for setting special parameters, such as resetting magnetic and electromagnetic influence screens

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                                 |
| ---- | ------- | ------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x64`                                                                   |
| `1`  | `uint8` | command size = `2`                                                                    |
| `1`  | `uint8` | operation type<br>`0x55` - reset reset magnetic and electromagnetic influence screens |
| `1`  | `uint8` | [operation parameters](#operation-parameters)                                         |

### Parameters

#### operation parameters for operation type `0x55`

Bit mask:

| Name                               | Bit | Description                                                                |
| ---------------------------------- | --- | -------------------------------------------------------------------------- |
| `RESET_ELECTROMAGNETIC_INDICATION` | `0` | Reset the electromagnetic influence screen if bit `7` is equal to zero     |
| `RESET_MAGNETIC_INDICATION`        | `1` | Reset the magnetic influence screen if bit `7` is equal to zero            |
| `READ_SCREENS_INFO`                | `7` | Read information about the presence of magnetic or electromagnetic screens |

### Examples

| Field                | Value                                                                                                             | Hex    |
| -------------------- | ----------------------------------------------------------------------------------------------------------------- | ------ |
| command id           | `100`                                                                                                             | `0x64` |
| command size         | `2`                                                                                                               | `0x02` |
| operation type       | `85`                                                                                                              | `0x55` |
| operation parameters | `RESET_ELECTROMAGNETIC_INDICATION`: `true`<br>`RESET_MAGNETIC_INDICATION`: `true`<br>`READ_SCREENS_INFO`: `false` | `0x03` |

Command hex dump: `64 02 85 03`


## Response

### Format

| Size | Type    | Field                                                                         |
| ---- | ------- | ----------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x64`                                                           |
| `1`  | `uint8` | command size = `1`                                                            |
| `1`  | `uint8` | [magnetic and electromagnetic screens](#magnetic-and-electromagnetic-screens) |

### Parameters

#### magnetic and electromagnetic screens

Bit mask:

| Name                     | Bit | Description                                 |
| ------------------------ | --- | ------------------------------------------- |
| `ELECTROMAGNETIC_SCREEN` | `0` | electromagnetic influence screen is present |
| `MAGNETIC_SCREEN`        | `1` | magnetic influence screen is present        |

### Examples

| Field                                | Value                                                         | Hex    |
| ------------------------------------ | ------------------------------------------------------------- | ------ |
| command id                           | `100`                                                         | `0x64` |
| command size                         | `1`                                                           | `0x01` |
| magnetic and electromagnetic screens | `ELECTROMAGNETIC_SCREEN`: `true`<br>`MAGNETIC_SCREEN`: `true` | `0x03` |

Command hex dump: `64 01 03`


## See also

* [Access level](../basics.md#command-access-level)
