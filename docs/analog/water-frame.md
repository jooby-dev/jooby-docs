# Water frame

It is used to communicate with ultrasonic water meters.

Frame format (each line is a byte):

<table>
    <tbody>
        <tr align="center">
            <td>frame size (including this byte)</td>
        </tr>
        <tr align="center">
            <td>function</td>
        </tr>
        <tr align="center">
            <td>attribute</td>
        </tr>
        <tr align="center">
            <td>arguments (optional)</td>
        </tr>
        <tr align="center">
            <td>...</td>
        </tr>
    </tbody>
</table>

See request/response encoding example for [Get_Volume](#get_volume).


## Error handling

For a failed request there is a special response in the following format:
length (`3` or `4` bytes) + function | `0x80` + attribute + error code.

Error codes:

| Error                     | Value |
| ------------------------- | ----- |
| `RESP_GENERAL_ERROR`      | `1`   |
| `RESP_INFO_ELEMENT_ERROR` | `2`   |
| `RESP_FUNC_NOT_FOUND`     | `3`   |
| `RESP_ATTR_NOT_FOUND`     | `4`   |
| `RESP_PARAMETER_ERROR`    | `5`   |

For example in case of wrong request `0x032401` (no such function `24`) the response is `0x04a40103` where

| Byte   | Description                      |
| ------ | -------------------------------- |
| `0x04` | size                             |
| `0xa4` | function `0x24` \| `0x80`        |
| `0x01` | attribute from request           |
| `0x03` | error code `RESP_FUNC_NOT_FOUND` |


## Attributes of WaterMonitor function

### Get_Info

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x01` - `0x032101`.

Response arguments:

| Size | Type     | Field                                    | Default    |
| ---- | -------- | ---------------------------------------- | ---------- |
| `2`  | `uint16` | software type of device                  | `0x1001`   |
| `8`  | `char`   | software version installed on the device | `00.01.01` |
| `2`  | `uint16` | hardware type of the device              | `0x0001`   |
| `8`  | `char`   | hardware revision of the device          | `00.00.01` |


### Get_Volume

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x02` - `0x032102`.

Response arguments:

| Size | Type    | Field              | Multiplier | Default |
| ---- | ------- | ------------------ | ---------- | ------- |
| `4`  | `int32` | forward flow value | `1`        | `0`     |
| `4`  | `int32` | reverse flow value | `1`        | `0`     |

Response example:

| Field         | Value          | Hex          |
| ------------- | -------------- | ------------ |
| size          | `11`           | `0x0b`       |
| function      | `WaterMonitor` | `0x21`       |
| attribute     | `Get_Volume`   | `0x02`       |
| forward value | `3`            | `0x00000003` |
| reverse value | `4`            | `0x00000004` |

Full payload: `0x0B21020000000300000004`.


### Get_FlowRate

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x03` - `0x032103`.

Response arguments:

| Size | Type    | Field     | Multiplier | Default |
| ---- | ------- | --------- | ---------- | ------- |
| `2`  | `int16` | flow rate | `1`        | `0`     |


### Get_OperatingTime

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x04` - `0x032104`.

Response arguments:

| Size | Type     | Field                                       | Multiplier | Default |
| ---- | -------- | ------------------------------------------- | ---------- | ------- |
| `4`  | `uint32` | total operating time, in seconds            | `1`        | `0`     |
| `4`  | `uint32` | operating time without an error, in seconds | `1`        | `0`     |


### Get_Battery

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x05` - `0x032105`.

Response arguments:

| Size | Type     | Field                 | Multiplier | Default |
| ---- | -------- | --------------------- | ---------- | ------- |
| `2`  | `uint16` | battery level, in `V` | `0.001`    | `0`     |


### Get_Status

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x06` - `0x032106`.

Response arguments:

| Size | Type      | Field      | Default |
| ---- | --------- | ---------- | ------- |
| `1`  | `bitmask` | status     | `0`     |
| `1`  | `uint8`   | error code | `0`     |

Status bitmask:

| Field         | Mask   |
| ------------- | ------ |
| transportMode | `0x01` |
| freqOut       | `0x02` |
| reverse       | `0x04` |
| tamper        | `0x08` |
| leak          | `0x10` |
| breakPipe     | `0x20` |
| emptyPipe     | `0x40` |
| discharge     | `0x80` |


### Get_Temperature

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x08` - `0x032108`.

Response arguments:

| Size | Type     | Field                      | Multiplier | Range     | Default |
| ---- | -------- | -------------------------- | ---------- | --------- | ------- |
| `2`  | `uint16` | water temperature, in `°C` | `0.1`      | `50..600` | `0`     |


### Get_SerialNumber

Request size `3`, function `WaterMonitor` (`0x21`), attribute `0x0b` - `0x03210b`.

Response arguments:

| Size | Type   | Field                | Default              |
| ---- | ------ | -------------------- | -------------------- |
| `18` | `char` | device serial number | `5001.00000000.2024` |


## Attributes of WaterMeter function

### Get_DepassivationLog

Request size `3`, function `WaterMeter` (`0x22`), attribute `0x1d` - `0x03221d`.

Response arguments:

| Size | Type     | Field                          | Multiplier | Range      | Default |
| ---- | -------- | ------------------------------ | ---------- | ---------- | ------- |
| `2`  | `uint16` | battery level high, in `V`     | `0.001`    | `0..4095`  | `0`     |
| `2`  | `uint16` | battery level low, in `V`      | `0.001`    | `0..4095`  | `0`     |
| `2`  | `uint16` | resistance, in `mΩ`            | `1`        | `0..65535` | `0`     |
| `2`  | `uint16` | depassivation time, in seconds | `1`        | `0..65535` | `0`     |
