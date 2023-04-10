# Specific types

Commands contain many specific types. Here - their explanation and structuring principles.

## Extended-bit value

For the values which can be small or large, commands used a format of the integer representation,
which minimizes bytes required for data transfer over communication channels.

The EXTEND bit is used for this.

 Bit index   | 8      | 7     | 6     | 5     | 4     | 3     | 2     | 1     |
-------------|--------|-------|-------|-------|-------|-------|-------|-------|
 description | EXTEND | value | value | value | value | value | value | value |

If the EXTEND bit set i.e. = `1`, this means that the next upper 7 bits of value will be placed in the next byte.
If EXTEND bit unset, i.e. = `0` will mean that this is the last byte with pulse counter data.

Max value in integer - 4 byte, 32 bit. Range from 1 to 5 bytes required to transfer value in messages.

### Examples

Representation of `131` integer value

 Bytes            | Extend bit set
------------------|----------------|
 `0x83`           | yes            |
 `0x01` size      | no             |
