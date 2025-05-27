# SetOpParamsExt4

Request/response to set device operator parameters `4`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                                    |
| ---- | -------- | ------------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x74`                                                      |
| `1`  | `uint8`  | command size = `28`                                                      |
| `4`  | `uint32` | [main mode display settings](./GetOpParamsExt4.md#display-settings)      |
| `4`  | `uint32` | [extended mode display settings](./GetOpParamsExt4.md#display-settings)  |
| `4`  | `uint32` | [battery mode display settings 1](./GetOpParams.md#display-settings-1)   |
| `4`  | `uint32` | [battery mode display settings 2](./GetOpParams.md#display-settings-2)   |
| `4`  | `uint32` | [battery mode display settings 3](./GetOpParams.md#display-settings-3)   |
| `4`  | `uint32` | [battery mode display settings 4](./GetOpParams.md#display-settings-4)   |
| `4`  | `uint32` | [battery mode display settings 5](./GetOpParamsExt4.md#display-settings) |

### Examples

<table>
  <thead>
    <tr>
      <th>Field</th>
      <th>Value</th>
      <th>Hex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>command id</td>
      <td><code>116</code></td>
      <td><code>0x74</code></td>
    </tr>
    <tr>
      <td>command size</td>
      <td><code>28</code></td>
      <td><code>0x1c</code></td>
    </tr>
    <tr>
      <td><a href="#display-settings">main mode display settings</a></td>
      <td><code>?</code></td>
      <td><code>0x0000005b</code></td>
    </tr>
    <tr>
      <td><a href="#display-settings">extended mode display settings</a></td>
      <td><code>?</code></td>
      <td><code>0x00000055</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-1">battery mode display settings 1</a></td>
      <td><code>?</code></td>
      <td><code>0x40040220</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-2">battery mode display settings 2</a></td>
      <td><code>?</code></td>
      <td><code>0x01000822</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-3">battery mode display settings 3</a></td>
      <td><code>?</code></td>
      <td><code>0x0c001018</code></td>
    </tr>
    <tr>
      <td><a href="./GetOpParams.md#display-settings-4">battery mode display settings 4</a></td>
      <td><code>?</code></td>
      <td><code>0x40180018</code></td>
    </tr>
    <tr>
      <td><a href="#display-settings">battery mode display settings 5</a></td>
      <td><code>?</code></td>
      <td><code>0x0000001c</code></td>
    </tr>
  </tbody>
</table>

Command hex dump: `74 1c 0000005b 00000055 40040220 01000822 0c001018 40180018 0000001c`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x74` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `116` | `0x74` |
| command size | `0`   | `0x00` |

Command hex dump: `75 00`


## See also

* [Access level](../basics.md#command-access-level)
