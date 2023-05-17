# Special data types

Commands use many specific data types packed to bytes.
This document describes these types and structuring principles.


## OBIS

It's an OBIS code packed in `3-7` bytes.
<br>
OBIS code contain 1 byte number (0-255) for 6 groups: A, B, C, D, E, F.
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

| group | value | hex    | bits       |
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

| group | value | hex    | bits         |
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
