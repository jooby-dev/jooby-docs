# Special data types

Commands use many specific data types packed to bytes.
This document describes these types and structuring principles.


## Extended value

This approach is good to minimize the amount of data that needs to be transmitted over communication channels.
It is used for data without fixed size using the minimum number of bytes with the help of `extend bit`.

Structure of a single byte with `extend bit`:

 8            | 7     | 6     | 5     | 4     | 3     | 2     | 1
--------------|-------|-------|-------|-------|-------|-------|---
 `extend bit` | value | value | value | value | value | value | value

When `extend bit` is set to `1` it means that the next byte will contain the next `7` most significant bits of the number.
On the other hand, when the `extend bit` is set to `0` it signifies that the current byte is the last byte containing the remaining data of the number.

To store a value bigger than `1` byte a sequence of bytes with `extend bit` is required.
For example `5` bytes are necessary for `32`-bit integer value (each line is a byte):

 `Extend bit` | Data bits range
--------------|-----------------
 `1`          | `6..0`
 `1`          | `13..7`
 `1`          | `20..14`
 `1`          | `27..21`
 `0`          | `31..28`

### Examples

Let's represent a value of `531` in this format.
`2` bytes are necessary for this.

Normal binary representation is `0b0000001000010011`. The same but in hex: `0x0213`.

To pack this value to extended value format it's necessary to take the first most right `7` bits - `0010011` and fill the first `7` bytes of the target byte. The `8`-th bit is the `extend bit` which shows there is more data to fill. So it should be `1`.
The first full byte now is `0b10010011` or `0x93`.

The next `7` bits are `0000100` and should be placed to the second target byte.
There are no significant bits left so no need to extend anymore and `extend bit` should be `0`.
The second full byte now is `0b00000100` or `0x04`.

The same in a table (each line is a byte):

 `Extend bit` | Data bits | Hex
--------------|-----------|-----
 `1`          | `0010011` | `0x93`
 `0`          | `0000100` | `0x04`

So `531` in extended value format is `0b0000010010010011` or `0x0493`.

Another example - `48` integer value which is `0b00110000` or `0x30`.

 `Extend bit` | Data bits | Hex
--------------|-----------|-----
 `0`          | `0110000` | `0x30`

As this value is less than `127` no extension is necessary and extended value is identical to the original one.

More complex example - `24214124` which is `0b00000001011100010111101001101100` or `0x01717a6c`.

 `Extend bit` | Data bits | Hex
--------------|-----------|-----
 `1`          | `1101100` | `0xec`
 `1`          | `1110100` | `0xf4`
 `1`          | `1000101` | `0xc5`
 `0`          | `0001011` | `0x0b`

Extended value is `0b00001011110001011111010011101100` or `0x0bc5f4ec`
