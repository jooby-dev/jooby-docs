# Special data types

Commands use many specific data types packed to bytes.
This document describes these types and structuring principles.


## Extended value

This approach is good to minimize the amount of data that needs to be transmitted over communication channels.
It is used for data without fixed size using the minimum number of bytes with the help of `extend bit`.

Structure of a single byte with `extend bit`:

| 8            | 7     | 6     | 5     | 4     | 3     | 2     | 1     |
| ------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| `extend bit` | value | value | value | value | value | value | value |

When `extend bit` is set to `1` it means that the next byte will contain the next `7` most significant bits of the number.
On the other hand, when the `extend bit` is set to `0` it signifies that the current byte is the last byte containing the remaining data of the number.

To store a value bigger than `1` byte a sequence of bytes with `extend bit` is required.
For example `5` bytes are necessary for `32-bit` integer value (each line is a byte):

| Extend bit | Data bits range |
| ---------- | --------------- |
| `1`        | `6..0`          |
| `1`        | `13..7`         |
| `1`        | `20..14`        |
| `1`        | `27..21`        |
| `0`        | `31..28`        |

### Examples

Let's represent a value of `531` in this format.
`2` bytes are necessary for this.

Normal binary representation is `0b0000001000010011`. The same but in hex: `0x0213`.

To pack this value to extended value format it's necessary to take the first most right `7` bits - `0010011` and fill the first `7` bytes of the target byte.
The `8`-th bit is the `extend bit` which shows there is more data to fill. So it should be `1`.
The first full byte now is `0b10010011` or `0x93`.

The next `7` bits are `0000100` and should be placed to the second target byte.
There are no significant bits left so no need to extend anymore and `extend bit` should be `0`.
The second full byte now is `0b00000100` or `0x04`.

The same in a table (each line is a byte):

| Extend bit | Data bits | Hex    |
| ---------- | --------- | ------ |
| `1`        | `0010011` | `0x93` |
| `0`        | `0000100` | `0x04` |

Please note that processing of the original value is done from right to left so to get the final value it's necessary to collect all bytes in reverse order.

Result: `531` in extended value format is `0x9304`.

Another example - `48` integer value which is `0x30`.

| Extend bit | Data bits | Hex    |
| ---------- | --------- | ------ |
| `0`        | `0110000` | `0x30` |

As this value is less than `127` no extension is necessary and extended value is identical to the original one.

More complex example - `24214124` which is `0b00000001011100010111101001101100` or `0x01717a6c`.

| Extend bit | Data bits | Hex    |
| ---------- | --------- | ------ |
| `1`        | `1101100` | `0xec` |
| `1`        | `1110100` | `0xf4` |
| `1`        | `1000101` | `0xc5` |
| `0`        | `0001011` | `0x0b` |

Extended value is `0xecf4c50b`.


## Time 2000

A `4`-byte value that indicates the number of seconds that have elapsed since the year `2000`.

### Examples

Time `2023-04-03T14:01:17.000Z` is `1680530477` in [Unix time](https://en.wikipedia.org/wiki/Unix_time) representation.
Unix time for year 2000 is `946684800` so seconds since year 2000 is `1680530477` - `946684800` = `733845677`.


## Packed date

It's a date value packed in `2` bytes.
Format (each line is a byte):

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
            <td colspan="7" align="center">Year [<code>7..0</code>]</td>
            <td align="center">Month [<code>3</code>]</td>
        </tr>
        <tr>
            <td colspan="3" align="center">Month [<code>2..0</code>]</td>
            <td colspan="5" align="center">Date [<code>4..0</code>]</td>
        </tr>
    </tbody>
</table>

### Examples

Let's pack the date `2023.12.23 00:00:00 GMT`.
<br/>
In order to set the year to `2023`, we need to calculate the difference between `2000` and `2023`.
It's `23` which is `0b10111`.
Pad this value with zeros till the necessary size of `7` bits.
Now it's `0b0010111` as the highest `7` bits of the first byte of the result.
<br/>
The month part `12` is `0b1100`.
The highest one bit should be placed to the position `0` of the first byte of the result. The rest `3` bits will be the highest bits of the second byte.
<br/>
The day part `23` is `0b10111`. It should be placed from the start of the first byte.
<br/>
Combine it all together to get `0b00101111` in the first byte and `0b10010111` in the second. The final value is `0x2f97`.

The same in a table form:

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
            <td colspan="7" align="center"><code>0010111</code></td>
            <td align="center"><code>1</code></td>
        </tr>
        <tr>
            <td colspan="3" align="center"><code>100</code></td>
            <td colspan="5" align="center"><code>10111</code></td>
        </tr>
    </tbody>
</table>


## Packed hours

It's a start hour value and the total number of hours packed in `1` byte.
The hours value `0` means `1` hours.
Format:

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
            <td colspan="3" align="center">Hours [<code>2..0</code>]</td>
            <td colspan="5" align="center">Hour [<code>4..0</code>]</td>
        </tr>
    </tbody>
</table>

### Examples

Let's pack the start hour `13:00` and the number of hour `2`.
<br/>
Hours `2` decreased by `1` (`0b1`) becomes `0b001` to have the size of `3` bits.
<br/>
Hour `13` (`0b1101`) becomes `0b01101` to have the size of `5` bits.
<br/>
Combine it all together to get `0b00101101` or `0x2d`.

The same in a table form:

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
            <td colspan="3" align="center"><code>010</code></td>
            <td colspan="5" align="center"><code>01101</code></td>
        </tr>
    </tbody>
</table>


## Packed magnetic influence and hour

It's a magnetic influence flag and start hour value packed in `1` byte.
Format:

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
            <td>magnetic influence</td>
            <td>reserved</td>
            <td>reserved</td>
            <td colspan="5" align="center">Hour [<code>4..0</code>]</td>
        </tr>
    </tbody>
</table>

### Examples

Let's pack the presence of magnetic influence and the start hour `09:00`.
<br/>
The presence of magnetic influence becomes `1` as the highest bit.
<br/>
Hour `09` (`0b1001`) becomes `0b01001` to have the size of `5` bits.
<br/>
Combine it all together to get `0b10001001` or `0x89`.

The same in a table form:

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
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td colspan="5" align="center"><code>01001</code></td>
        </tr>
    </tbody>
</table>


## Packed magnetic influence and diff

It's a magnetic influence flag and hourly difference in readings packed in `2` bytes.
Format:

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
            <td>magnetic influence</td>
            <td>reserved</td>
            <td>reserved</td>
            <td colspan="5" align="center">diff value [<code>12..8</code>]</td>
        </tr>
        <tr>
            <td colspan="8" align="center">diff value [<code>7..0</code>]</td>
        </tr>
    </tbody>
</table>

### Examples

Let's pack the presence of magnetic influence and the hourly difference value `348`.
<br/>
The presence of magnetic influence becomes `1` as the highest bit.
<br/>
Value `348` (`0b101011100`) splits to two bytes `0b1` and `0b01011100`.
<br/>
Combine it all together to get `0b1000000101011100` or `0x815c`.

The same in a table form:

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
            <td><code>1</code></td>
            <td><code>0</code></td>
            <td><code>0</code></td>
            <td colspan="5" align="center"><code>00001</code></td>
        </tr>
        <tr>
            <td colspan="8" align="center"><code>01011100</code></td>
        </tr>
    </tbody>
</table>


## Channels bit set

[Extended value](#extended-value) that stores bit set of all channels indexes in command.
Each bit represents one channel.
If in some position some bit is `1` then data is present.
Note that bit position `0` is for channel number `1`.
If bits `0`, `1`, `2`, `3` are set - this means that values from that channels in that order are stored in the command (channels `1`, `2`, `3`, `4`).
The data for channel at `0` position comes first, then the second, the third and so on.
To store up to `7` channels `1` byte is required. To store up to `14` - `2` bytes and so on.
Usually this bit set takes from `1` to `5` bytes as there are 4 channels max available.

### Examples

#### 4 first channels:

One byte `0b00001111` which is the same with extended bits or `0x0f`.

#### channels `6`, `7`, `13`:

Two bytes `0b0001000001100000`. It becomes `0b0010000011100000` with extended bits or `0xe020`.


## Channel values

It's a sequence of [extended values](#extended-value) to store channel values.
Each value usually is up to `32-bit` integer.

### Examples

#### 4 channels with values `131`, `8`, `10`, `12`

The first value `131` is `0b0000000010000011` with extended bits becomes `0b0000000110000011` or `0x8301`.
All the rest values are simple (extended bit is `0`) and take one byte each.
<br/>
The final sequence is `83 01 08 0a 0c`.

#### 3 channels with values `8146`, `164`, `75`

The first value `8146` is `0b0001111111010010` with extended bits becomes `0b0011111111010010` or `0xd23f`.
The second value `164` is `0b0000000010100100` with extended bits becomes `0b0000000110100100` or `0xa401`.
The last value `75` is simple (no extension) `0x4b`.
<br/>
The final sequence is `e0 20 d2 3f a4 01 4b`.


# Pulse coefficient

It's `1`-byte value of the pulse coefficient for a metering device, which determines the correspondence of consumed resources to 1 pulse.
If the most significant bit is `0`, then the remaining `7` bits represent the value of the pulse coefficient,
i.e. `0x0A` (`10`) for `10` cubic decimeters = `10` liters = `0.01` cubic meters per pulse.
If the most significant bit is `1` then the value of pulse coefficient is determined from the table:

| Pulse coefficient | dm<sup>3</sup> | m<sup>3</sup> |
| ----------------- | -------------- | ------------- |
| `0х80`            | `1`            | `0.001`       |
| `0х81`            | `5`            | `0.005`       |
| `0х82`            | `10`           | `0.01`        |
| `0х83`            | `100`          | `0.1`         |
| `0х84`            | `1000`         | `1`           |
| `0х85`            | `10000`        | `10`          |
| `0х86`            | `100000`       | `100`         |
