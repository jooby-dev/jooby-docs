# Special data types

Commands use many specific data types packed to bytes.
This document describes these types and structuring principles.
It's applicable to both MTX1 and MTX3 devices.


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
