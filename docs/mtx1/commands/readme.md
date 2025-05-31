# Commands

There are `2` types of command direction:

- `downlink` - request (sent from server to device)
- `uplink` - response or event (sent from device to server)

<table>
    <thead>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Access level</th>
            <th>Links</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>0x01</code></td>
            <td><code>GetEventStatus</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEventStatus.md#request">request</a> / <a href="./GetEventStatus.md#response">response</a></td>
            <td>Get the device status events.</td>
        </tr>
        <tr>
            <td><code>0x03</code></td>
            <td><code>GetEnergyDayPrevious</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEnergyDayPrevious.md#request">request</a> / <a href="./GetEnergyDayPrevious.md#response">response</a></td>
            <td>Get the previous day energy `A+` for `4` tariffs.</td>
        </tr>
        <tr>
            <td><code>0x04</code></td>
            <td><code>GetDeviceType</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDeviceType.md#request">request</a> / <a href="./GetDeviceType.md#response">response</a></td>
            <td>Get the device type.</td>
        </tr>
        <tr>
            <td><code>0x05</code></td>
            <td><code>GetDeviceId</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDeviceId.md#request">request</a> / <a href="./GetDeviceId.md#response">response</a></td>
            <td>Get the device identifier.</td>
        </tr>
        <tr>
            <td><code>0x06</code></td>
            <td><code>RunTariffPlan</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./RunTariffPlan.md#request">request</a> / <a href="./RunTariffPlan.md#response">response</a></td>
            <td>Instant activation of the passive tariff plan.</td>
        </tr>
        <tr>
            <td><code>0x07</code></td>
            <td><code>GetDateTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDateTime.md#request">request</a> / <a href="./GetDateTime.md#response">response</a></td>
            <td>Get the device full date and time with <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a> flag.</td>
        </tr>
        <tr>
            <td><code>0x08</code></td>
            <td><code>SetDateTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./SetDateTime.md#request">request</a> / <a href="./SetDateTime.md#response">response</a></td>
            <td>Set the device full date and time with <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a> flag.</td>
        </tr>
        <tr>
            <td><code>0x09</code></td>
            <td><code>SetAccessKey</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetAccessKey.md#request">request</a> / <a href="./SetAccessKey.md#response">response</a></td>
            <td>Set the device access key.</td>
        </tr>
        <tr>
            <td><code>0x0d</code></td>
            <td><code>GetCurrentValues</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetCurrentValues.md#request">request</a> / <a href="./GetCurrentValues.md#response">response</a></td>
            <td>Get current values like voltage, power, etc.</td>
        </tr>
        <tr>
            <td><code>0x0f</code></td>
            <td><code>GetEnergy</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEnergy.md#request">request</a> / <a href="./GetEnergy.md#response">response</a></td>
            <td>Get current energy <code>A+</code> by default or selected energy type for 4 tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x10</code></td>
            <td><code>SetDayProfile</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetDayProfile.md#request">request</a> / <a href="./SetDayProfile.md#response">response</a></td>
            <td>Set day profile information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x12</code></td>
            <td><code>SetSpecialDay</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetSpecialDay.md#request">request</a> / <a href="./SetSpecialDay.md#response">response</a></td>
            <td>Set special day information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x13</code></td>
            <td><code>ActivateRatePlan</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./ActivateRatePlan.md#request">request</a> / <a href="./ActivateRatePlan.md#response">response</a></td>
            <td>Provide the date and parameters of tariff plan activation.</td>
        </tr>
        <tr>
            <td><code>0x14</code></td>
            <td><code>PrepareRatePlan</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./PrepareRatePlan.md#request">request</a> / <a href="./PrepareRatePlan.md#response">response</a></td>
            <td>Prepare device for rate plan application.</td>
        </tr>
        <tr>
            <td><code>0x15</code></td>
            <td><code>GetHalfHourDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemand.md#request">request</a> / <a href="./GetHalfHourDemand.md#response">response</a></td>
            <td>Get active energy (<code>A+</code>) in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x18</code></td>
            <td><code>TurnRelayOn</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./TurnRelayOn.md#request">request</a> / <a href="./TurnRelayOn.md#response">response</a></td>
            <td>Turn the device relay on.</td>
        </tr>
        <tr>
            <td><code>0x19</code></td>
            <td><code>TurnRelayOff</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./TurnRelayOff.md#request">request</a> / <a href="./TurnRelayOff.md#response">response</a></td>
            <td>Turn the device relay off.</td>
        </tr>
        <tr>
            <td><code>0x1c</code></td>
            <td><code>SetCorrectTime</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetCorrectTime.md#request">request</a> / <a href="./SetCorrectTime.md#response">response</a></td>
            <td>Set <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a>/Standard time transition options.</td>
        </tr>
        <tr>
            <td><code>0x1e</code></td>
            <td><code>GetOperatorParameters</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetOperatorParameters.md#request">request</a> / <a href="./GetOperatorParameters.md#response">response</a></td>
            <td>Get device operator parameters.</td>
        </tr>
        <tr>
            <td><code>0x1f</code></td>
            <td><code>SetOperatorParameters</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetOperatorParameters.md#request">request</a> / <a href="./SetOperatorParameters.md#response">response</a></td>
            <td>Set device operator parameters.</td>
        </tr>
        <tr>
            <td><code>0x28</code></td>
            <td><code>GetVersion</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetVersion.md#request">request</a> / <a href="./GetVersion.md#response">response</a></td>
            <td>Get device version information.</td>
        </tr>
        <tr>
            <td><code>0x29</code></td>
            <td><code>GetSaldo</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetSaldo.md#request">request</a> / <a href="./GetSaldo.md#response">response</a></td>
            <td>Get device current saldo information.</td>
        </tr>
        <tr>
            <td><code>0x2a</code></td>
            <td><code>SetSaldo</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetSaldo.md#request">request</a> / <a href="./SetSaldo.md#response">response</a></td>
            <td>Set device current saldo information.</td>
        </tr>
        <tr>
            <td><code>0x2c</code></td>
            <td><code>GetRatePlanInfo</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetRatePlanInfo.md#request">request</a> / <a href="./GetRatePlanInfo.md#response">response</a></td>
            <td>Get device rate plan information.</td>
        </tr>
        <tr>
            <td><code>0x2e</code></td>
            <td><code>GetSaldoParameters</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetSaldoParameters.md#request">request</a> / <a href="./GetSaldoParameters.md#response">response</a></td>
            <td>Get device current saldo parameters information.</td>
        </tr>
        <tr>
            <td><code>0x2f</code></td>
            <td><code>SetSaldoParameters</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetSaldoParameters.md#request">request</a> / <a href="./SetSaldoParameters.md#response">response</a></td>
            <td>Set device current saldo parameters information.</td>
        </tr>
        <tr>
            <td><code>0x31</code></td>
            <td><code>GetDayMaxDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayMaxDemand.md#request">request</a> / <a href="./GetDayMaxDemand.md#response">response</a></td>
            <td>Get the maximum daily power <code>P+</code> for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x33</code></td>
            <td><code>GetEvents</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEvents.md#request">request</a> / <a href="./GetEvents.md#response">response</a></td>
            <td>Get events.</td>
        </tr>
        <tr>
            <td><code>0x34</code></td>
            <td><code>GetEventsCounter</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEventsCounter.md#request">request</a> / <a href="./getEventsCounter.md#response">response</a></td>
            <td>Get events counters.</td>
        </tr>
        <tr>
            <td><code>0x35</code></td>
            <td><code>ResetPowerMaxDay</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./ResetPowerMaxDay.md#request">request</a> / <a href="./ResetPowerMaxDay.md#response">response</a></td>
            <td>Reset daily max power.</td>
        </tr>
        <tr>
            <td><code>0x36</code></td>
            <td><code>ResetPowerMaxMonth</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./ResetPowerMaxMonth.md#request">request</a> / <a href="./ResetPowerMaxMonth.md#response">response</a></td>
            <td>Reset for monthly max power.</td>
        </tr>
        <tr>
            <td><code>0x3a</code></td>
            <td><code>GetExtendedCurrentValues</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetExtendedCurrentValues.md#request">request</a> / <a href="./GetExtendedCurrentValues.md#response">response</a></td>
            <td>Get the temperature and supply frequency.</td>
        </tr>
        <tr>
            <td><code>0x3b</code></td>
            <td><code>GetDayProfile</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayProfile.md#request">request</a> / <a href="./GetDayProfile.md#response">response</a></td>
            <td>Get day profile information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x3d</code></td>
            <td><code>GetSpecialDay</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="GetSpecialDay.md#request">request</a> / <a href="GetSpecialDay.md#response">response</a></td>
            <td>Get special day information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x3e</code></td>
            <td><code>GetCorrectTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetCorrectTime.md#request">request</a> / <a href="./GetCorrectTime.md#response">response</a></td>
            <td>Get <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a>/Standard time transition options.</td>
        </tr>
        <tr>
            <td><code>0x41</code></td>
            <td><code>GetCriticalEvent</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetCriticalEvent.md#request">request</a> / <a href="./GetCriticalEvent.md#response">response</a></td>
            <td>Get device critical events.</td>
        </tr>
        <tr>
            <td><code>0x50</code></td>
            <td><code>GetExportEnergyDayPrevious</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetExportEnergyDayPrevious.md#request">request</a> / <a href="./GetExportEnergyDayPrevious.md#response">response</a></td>
            <td>Get the previous day energy `A-` for `4` tariffs.</td>
        </tr>
        <tr>
            <td><code>0x53</code></td>
            <td><code>GetHalfHourDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandExport.md#request">request</a> / <a href="./GetHalfHourDemandExport.md#response">response</a></td>
            <td>Get active energy (<code>A-</code>) in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x58</code></td>
            <td><code>GetDayMaxDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayMaxDemandExport.md#request">request</a> / <a href="./GetDayMaxDemandExport.md#response">response</a></td>
            <td>Get the maximum daily power <code>P-</code> for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x5c</code></td>
            <td><code>SetCorrectDateTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./SetCorrectDateTime.md#request">request</a> / <a href="./SetCorrectDateTime.md#response">response</a></td>
            <td>Incremental device time correction (for a given number of seconds).</td>
        </tr>
        <tr>
            <td><code>0x5d</code></td>
            <td><code>SetDisplayParam</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetDisplayParam.md#request">request</a> / <a href="./SetDisplayParam.md#response">response</a></td>
            <td>Set the meter displays sorting order.</td>
        </tr>
        <tr>
            <td><code>0x5e</code></td>
            <td><code>GetDisplayParam</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDisplayParam.md#request">request</a> / <a href="./GetDisplayParam.md#response">response</a></td>
            <td>Get the meter displays sorting order.</td>
        </tr>
        <tr>
            <td><code>0x64</code></td>
            <td><code>SetSpecialOperation</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetSpecialOperation.md#request">request</a> / <a href="./SetSpecialOperation.md#response">response</a></td>
            <td>Set special parameters.</td>
        </tr>
        <tr>
            <td><code>0x6d</code></td>
            <td><code>GetMagneticFieldThreshold</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetMagneticFieldThreshold.md#request">request</a> / <a href="./GetMagneticFieldThreshold.md#response">response</a></td>
            <td>Get parameters related to magnetic field detection.</td>
        </tr>
        <tr>
            <td><code>0x70</code></td>
            <td><code>GetBuildVersion</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetBuildVersion.md#request">request</a> / <a href="./GetBuildVersion.md#response">response</a></td>
            <td>Get firmware build date and version from device.</td>
        </tr>
        <tr>
            <td><code>0x71</code></td>
            <td><code>GetOperatorParametersExt3</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetOperatorParametersExt3.md#request">request</a> / <a href="./GetOperatorParametersExt3.md#response">response</a></td>
            <td>Get extended device operator parameters <code>3</code>.</td>
        </tr>
        <tr>
            <td><code>0x72</code></td>
            <td><code>SetOperatorParametersExt3</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetOperatorParametersExt3.md#request">request</a> / <a href="./SetOperatorParametersExt3.md#response">response</a></td>
            <td>Set extended device operator parameters <code>3</code>.</td>
        </tr>
        <tr>
            <td><code>0x78</code></td>
            <td><code>GetDayEnergies</code></td>
            <td><code>UNENCRYPTED</code></td>
            <td><a href="./uplink/GetDayEnergies.md">event</a></td>
            <td>Event to get day energies by <code>4</code> tariffs (<code>T1</code>-<code>T4</code>). Can be transmitted only via Lora.</td>
        </tr>
        <tr>
            <td><code>0x7a</code></td>
            <td><code>GetMeterInfo</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetMeterInfo.md#request">request</a> / <a href="./GetMeterInfo.md#response">response</a></td>
            <td>Get meter info.</td>
        </tr>
        <tr>
            <td><code>0xfe</code></td>
            <td><code>ErrorResponse</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./ErrorResponse.md#response">response</a></td>
            <td>Provide info for the failed downlink command.</td>
        </tr>
    </tbody>
</table>


**Note**

All number fields in the commands are transmitted in big-endian format.
