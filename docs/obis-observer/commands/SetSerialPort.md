# SetSerialPort

Request/response to set serial port parameters.


## Request

### Format

| Size | Type                                 | Field                                                      |
| ---- | ------------------------------------ | ---------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x07`                                        |
| `1`  | `byte`                               | command size                                               |
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
            <td colspan="6"><code>0</code></td>
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

| Field        | Value         | Hex    |
| ------------ | ------------- | ------ |
| command id   | `19`          | `0x07` |
| command size | `4`           | `0x04` |
| request id   | `52`          | `0x34` |
| baud rate    | `9600`        | `0x05` |
| data bits    | `8`           | `0x08` |
| flags        | parity: `odd` | `0x01` |

Message hex dump: `07 04 34 05 08 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x08`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `8`   | `0x08` |
| command size | `1`   | `0x01` |
| request id   | `32`  | `0x20` |

Message hex dump: `08 01 20`


#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description   |
| ----------- | ------------- |
| `3`         | Format error. |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
