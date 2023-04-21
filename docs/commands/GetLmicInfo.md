# GetLmicInfo

Command to get LMiC (IBM LoRaWAN in C) information.


## Request

### Format

| Size | Type | Field               |
| ---- | ---- | ------------------- |
| `1`  | byte | extra flag = `0x1f` |
| `1`  | byte | command id = `0x02` |
| `1`  | byte | command size = `0`  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `2`   | `0x02` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 02 00 48`


## Response

It's a mandatory confirmation to [GetLmicInfo request](./GetLmicInfo.md#request).

### Format

| Size | Type | Field                         |
| ---- | ---- | ----------------------------- |
| `1`  | byte | extra flag = `0x1f`           |
| `1`  | byte | command id = `0x02`           |
| `1`  | byte | length = `2`                  |
| `1`  | byte | [capabilities](#capabilities) |
| `1`  | byte | [version](#version)           |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **capabilities**

LMiC capabilities bit set.

| Bit | Description                                                                                                                               |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `0` | `1` - has [multicast](https://lora-alliance.org/resource_hub/lorawan-remote-multicast-setup-specification-v1-0-0/) support                |
| `1` | `1` - has [fragmented data](https://lora-alliance.org/resource_hub/lorawan-fragmented-data-block-transport-specification-v1-0-0/) support |

#### **version**

LMiC version.

### Examples

| Field        | Value                                     | Bits         | Hex    |
| ------------ | ----------------------------------------- | ------------ | ------ |
| extra flag   | `31`                                      |              | `0x1f` |
| command id   | `2`                                       |              | `0x02` |
| command size | `2`                                       |              | `0x02` |
| capabilities | no multicast, has fragmented data support | `0b00000010` | `0x02` |
| version      | `8`                                       |              | `0x08` |

Message hex dump with LRC: `1f 02 02 02 08 40`
