# Message format

Devices send and receive messages in the following format:

<table>
    <tbody>
        <tr align="center">
            <td>Command 1</td>
        </tr>
        <tr align="center">
            <td>Command 2</td>
        </tr>
        <tr align="center">
            <td>...</td>
        </tr>
        <tr align="center">
            <td>Command N</td>
        </tr>
        <tr align="center">
            <td>LRC</td>
        </tr>
    </tbody>
</table>

The `LRC` is calculated by performing an XOR operation on the content of the message with the start value `0x55`.


## Commands

Each [command](./commands/readme.md) consists of header and optional data body.

There can be `3` types of headers in commands.

### Command with a one-byte header

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
            <td colspan="3" align="center">command id</td>
            <td colspan="5" align="center">command data size</td>
        </tr>
        <tr>
            <td colspan="8" align="center">command data</td>
        </tr>
    </tbody>
</table>

### Command with a two-bytes header

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
            <td>0</td>
            <td>0</td>
            <td>0</td>
            <td colspan="5" align="center">command id</td>
        </tr>
        <tr>
            <td colspan="8" align="center">command data size</td>
        </tr>
        <tr>
            <td colspan="8" align="center">command data</td>
        </tr>
    </tbody>
</table>

### Command with a three-bytes header

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
            <td colspan="8" align="center"><code>0x1f</code></td>
        </tr>
        <tr>
            <td colspan="8" align="center">command id</td>
        </tr>
        <tr>
            <td colspan="8" align="center">command data size</td>
        </tr>
        <tr>
            <td colspan="8" align="center">command data</td>
        </tr>
    </tbody>
</table>
