# GetDeviceId

Request/response to get the device identifier.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x05` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `5`   | `0x05` |
| command size | `0`   | `0x00` |

Command hex dump: `05 00`


## Response

### Format

| Size | Type    | Field                                           |
| ---- | ------- | ----------------------------------------------- |
| `1`  | `uint8` | command id = `0x05`                             |
| `1`  | `uint8` | command size = `8`                              |
| `3`  | `uint8` | manufacturer (as string `001a79` at the moment) |
| `1`  | `uint8` | [type](#type)                                   |
| `1`  | `uint8` | year (number of years after `2000`)             |
| `3`  | `uint8` | serial (as string, e.g. `1b1d6a`)               |

### Parameters

#### type

One of the following device types:

| ID   | Name                                   |
| ---- | -------------------------------------- |
| `01` | MTX 1                                  |
| `02` | MTX 3 direct (old)                     |
| `03` | MTX 3 transformer (old)                |
| `04` | MTX 3 direct                           |
| `05` | MTX 3 transformer                      |
| `11` | MTX 1 new (two shunts)                 |
| `12` | MTX 3 direct new (shunts)              |
| `13` | MTX 3 transformer new                  |
| `14` | MTX 1 pole                             |
| `15` | MTX RD remote display                  |
| `16` | MTX RR repeater                        |
| `21` | MTX 1 new, current transformers        |
| `22` | MTX 3 direct new, current transformers |
| `80` | RF module                              |
| `81` | water meter                            |

### Examples

| Field        | Value                         | Hex        |
| ------------ | ----------------------------- | ---------- |
| command id   | `5`                           | `0x05`     |
| command size | `8`                           | `0x08`     |
| manufacturer | `001a79`                      | `0x001a79` |
| type         | `05` (MTX 3 transformer)      | `0x05`     |
| year         | `20` (`2000` + `20` = `2020`) | `0x14`     |
| serial       | `1b1d6a`                      | `0x1b1d6a` |

Command hex dump: `05 08 00 1a 79 05 14 1b 1d 6a`


## See also

* [Access level](../basics.md#command-access-level)
