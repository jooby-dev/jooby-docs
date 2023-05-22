# SetSerialPort

Request/response to set serial port parameters.


## Request

### Format

| Size | Type                                 | Field                                                      |
| ---- | ------------------------------------ | ---------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x13`                                        |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                         |
| `1`  | `byte`                               | [baud rate](#baud-rate)                                    |
| `1`  | `byte`                               | serial port word length or data bits (supported: `7`, `8`) |
| `1`  | `byte`                               | [flags](#flags)                                            |

### Parameters

#### **baud rate**

The serial port baud rate.

| Value | Baud rate |
| ----- | --------- |
| `0`   | `300`     |
| `1`   | `600`     |
| `2`   | `1200`    |
| `3`   | `2400`    |
| `4`   | `4800`    |
| `5`   | `9600`    |
| `6`   | `14440`   |
| `7`   | `19200`   |
| `8`   | `28800`   |
| `9`   | `38400`   |
| `10`  | `56000`   |
| `11`  | `57600`   |
| `12`  | `115200`  |

#### **flags**

The serial port parity setting.

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
            <td colspan="5"><code>0</code></td>
            <td>
                fixed flag: <br>
                <code>0</code> - the given setting will be used as initial <br>
                <code>1</code> - only the given settings will be used
            </td>
            <td colspan="2">
                parity: <br>
                <code>0</code> - none <br>
                <code>1</code> - odd <br>
                <code>2</code> - even <br>
            </td>
        </tr>
    </tbody>
</table>

### Examples

#### set fixed settings:

| Field      | Value                               | Hex    |
| ---------- | ----------------------------------- | ------ |
| command id | `19`                                | `0x13` |
| request id | `52`                                | `0x34` |
| baud rate  | `9600`                              | `0x05` |
| data bits  | `8`                                 | `0x08` |
| flags      | parity: `odd` <br> is fixed: `true` | `0x05` |

Message hex dump: `13 34 05 08 05`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x14`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |

### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `20`  | `0x14` |
| request id  | `32`  | `0x20` |
| result code | `OK`  | `0x00` |

Message hex dump: `14 20 00`

#### failure:

| Field       | Value     | Hex    |
| ----------- | --------- | ------ |
| command id  | `20`      | `0x14` |
| request id  | `32`      | `0x20` |
| result code | `FAILURE` | `0x01` |

Message hex dump: `14 20 01`


## See also

* [Request ID](../types.md#request-id)
* [Short name](../types.md#short-name)
* [OBIS code](../types.md#obis)
* [Result code](../types.md#result-code)
