# Special data types

Commands use many specific data types packed to bytes.
This document describes these types and structuring principles.


## Short name

A `1`-byte number will be used in all messages to represent the specific OBIS code.
See the full list of [short names](short-names.md).


## Time 2000

A `4`-byte value that indicates the number of seconds that have elapsed since the year `2000`.

### Examples

Time `2023-04-03T14:01:17.000Z` is `1680530477` in [Unix time](https://en.wikipedia.org/wiki/Unix_time) representation.
Unix time for year 2000 is `946684800` so seconds since year 2000 is `1680530477` - `946684800` = `733845677`.


## String

| Size | Type   | Field          |
| ---- | ------ | -------------- |
| `1`  | `byte` | string size    |
| `1+` | `byte` | string content |


## OBIS

It's an OBIS code packed in `3-7` bytes.
<br>
OBIS code contain `1` byte number (`0`-`255`) for `6` groups: A, B, C, D, E, F.
<br>
OBIS code represents in format: `A-B*C.D.E*F`

Structure of a OBIS bytes:

<table>
    <thead>
        <tr>
            <th>8</th>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan=4 align="center">0</td>
            <td>A group flag</td>
            <td>B group flag</td>
            <td>E group flag</td>
            <td>F group flag</td>
        </tr>
        <tr>
            <td colspan=8>A group value</td>
        </tr>
        <tr>
            <td colspan=8>B group value</td>
        </tr>
        <tr>
            <td colspan=8>C group value</td>
        </tr>
        <tr>
            <td colspan=8>D group value</td>
        </tr>
        <tr>
            <td colspan=8>E group value</td>
        </tr>
        <tr>
            <td colspan=8>F group value</td>
        </tr>
    </tbody>
</table>


When `group flag` bit is set, it means that the specified byte will contain group value, exception only for groups C, D - they always exists.


### Examples

Let's represent a OBIS code `1-0:11.35.0*0` in this format.
`4` bytes are necessary for this.

The group values:

| Group | Value | Hex    | Bits       |
| ----- | ----- | ------ | ---------- |
| `A`   | `1`   | `0x01` | `0b1`      |
| `B`   | `0`   |        |            |
| `C`   | `11`  | `0x0b` | `0b1011`   |
| `D`   | `35`  | `0x23` | `0b100011` |
| `E`   | `0`   |        |            |
| `F`   | `0`   |        |            |

Bytes representation in table form:

<table>
    <thead>
        <tr>
            <th>8</th>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="4"><code>0</code></td>
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
        </tr>
        <tr>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
        </tr>
        <tr>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
        </tr>
        <tr>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
        </tr>
    </tbody>
</table>

Result: `1-0:11.35.0*0` in hex `0x08010b23`.


Another example - for OBIS code `7-0:41.0.0*255`
`5` bytes are necessary for this.

The group values:

| Group | Value | Hex    | Bits         |
| ----- | ----- | ------ | ------------ |
| `A`   | `7`   | `0x07` | `0b111`      |
| `B`   | `0`   |        |              |
| `C`   | `41`  | `0x29` | `0b101001`   |
| `D`   | `0`   | `0x00` | `0b0`        |
| `E`   | `0`   |        |              |
| `F`   | `255` | `0xff` | `0b11111111` |

Bytes representation in table form:

<table>
    <thead>
        <tr>
            <th>8</th>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="4"><code>0</code></td>
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
        </tr>
        <tr>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
        </tr>
        <tr>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>1</code></td>
        </tr>
        <tr>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
        </tr>
        <tr>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
            <td><code>1</code></td>
        </tr>
    </tbody>
</table>

Result: `7-0:41.0.0*255` in hex `0x09072900ff`.


## OBIS profile

| Size | Type        | Field                                                                                                                                 |
| ---- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `2`  | `uint16_be` | Capture period in minutes. This determines how often the OBIS observer will read the value of the OBIS code from the metering device. |
| `2`  | `uint16_be` | Sending period in minutes.                                                                                                            |
| `1`  | `byte`      | Sending counter.                                                                                                                      |
| `1`  | `byte`      | [OBIS profile flags](#obis-profile-flags)                                                                                             |

### OBIS profile flags

<table>
    <thead>
        <tr>
            <th>8</th>
            <th>7</th>
            <th>6</th>
            <th>5</th>
            <th>4</th>
            <th>3</th>
            <th>2</th>
            <th>1</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="3"><code>0</code></td>
            <td colspan="2"><a href="#contenttype">ContentType</a></td>
            <td>sendingOnlyIfChange</td>
            <td colspan="2"><a href="#archivetype">ArchiveType</a></td>
        </tr>
    </tbody>
</table>

### ContentType

| Value | Description                |
| ----- | -------------------------- |
| `0`   | auto (auto-detection type) |
| `1`   | float                      |
| `2`   | string                     |

### ArchiveType

| Value | Description                                                                                                                                                                         |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0`   | No archive. The data will not be archived.                                                                                                                                          |
| `1`   | Detailed archive. This archive contains data that is captured at a highly detailed level, providing a granular view of performance. By default, the archive period is `15` minutes. |
| `2`   | Summary archive. The archive contains data that has been collected over a long interval. By default, the archive period is one day.                                                 |


## Result code

| Value | Description                                                      |
| ----- | ---------------------------------------------------------------- |
| `0`   | Ok. The Operation was successful.                                |
| `1`   | General failure.                                                 |
| `2`   | Forbidden to reassign the static short name.                     |
| `3`   | The short name to OBIS code map full: unable to add new entries. |
| `4`   | Short name not found.                                            |
| `5`   | Profile not found.                                               |
