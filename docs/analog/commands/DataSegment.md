# DataSegment

Transfer data by breaking it into segments.
This command is currently used only in module with [hardware type](../basics.md#hardware-types) `MTXLora`.
This command could be used as uplink or downlink command. The module can send `DataSegment` command as the response to the request or
without any request.


## Request

### Format

| Size | Type    | Field                                               |
| ---- | ------- | --------------------------------------------------- |
| `1`  | `uint8` | command id = `0x1e`                                 |
| `1`  | `uint8` | command size (dynamic, `2+`)                        |
| `1`  | `uint8` | [segmentation session id](#segmentation-session-id) |
| `1`  | `uint8` | [segment flags](#segment-flags)                     |
| `1+` | `uint8` | data (array of bytes)                               |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **segment flags**

<table>
    <thead>
        <tr>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
            <th>0</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><a href="#last-segment">last segment</a></td>
            <td colspan="3" align="center"><a href="#segments-number">segments number</a></td>
            <td>spare</td>
            <td colspan="3" align="center"><a href="#segment-index">segment index</a></td>
        </tr>
    </tbody>
</table>

#### **segmentation session id**

Represents a unique identifier for a session during which segments are collected. All segments belonging to the same message share the same `segmentationSessionId`, allowing the collector to correlate and assemble them correctly.

#### **last segment**

It is a boolean flag which indicates that a particular segment is the last in the sequence of segments that collectively form a complete message.

#### **segments number**

Specifies the total number of segments that make up the complete message.

#### **segment index**

Denotes the index or position of a particular segment within the entire message.

### Examples

| Field                   | Value                                                                  | Bits         | Hex                |
| ----------------------- | ---------------------------------------------------------------------- | ------------ | ------------------ |
| command id              | `30`                                                                   |              | `0x1e`             |
| command size            | `9`                                                                    |              | `0x09`             |
| segmentation session id | `35`                                                                   |              | `0x23`             |
| segment flags           | last segment: `true` <br> segments number: `1` <br> segment index: `1` | `0b10010001` | `0x91`             |
| data                    | `23 10 10 07 00 00 00`                                                 |              | `0x23101007000000` |

Message hex dump: `1e 09 23 91 23 10 10 07 00 00 00`


## Response

The response has the same format as the [request](#request).


## See also

* [hardware type](../basics.md#hardware-types)
* [two-bytes header](../message.md#command-with-a-two-bytes-header)
