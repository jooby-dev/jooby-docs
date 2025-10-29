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
            <td><a href="../../mtx1/commands/GetEventStatus.md#request">request</a> / <a href="../../mtx1/commands/GetEventStatus.md#response">response</a></td>
            <td>Get the device status events.</td>
        </tr>
        <tr>
            <td><code>0x03</code></td>
            <td><code>GetEnergyDayPrevious</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEnergyDayPrevious.md#request">request</a> / <a href="./GetEnergyDayPrevious.md#response">response</a></td>
            <td>Get the previous day active energy <code>A+, R+, R-</code> for all tariffs (<code>T1</code>-<code>T4</code>).</td>
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
            <td><a href="../../mtx1/commands/GetDeviceId.md#request">request</a> / <a href="../../mtx1/commands/GetDeviceId.md#response">response</a></td>
            <td>Get the device identifier.</td>
        </tr>
        <tr>
            <td><code>0x06</code></td>
            <td><code>RunTariffPlan</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/RunTariffPlan.md#request">request</a> / <a href="../../mtx1/commands/RunTariffPlan.md#response">response</a></td>
            <td>Instant activation of the passive tariff plan.</td>
        </tr>
        <tr>
            <td><code>0x07</code></td>
            <td><code>GetDateTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetDateTime.md#request">request</a> / <a href="../../mtx1/commands/GetDateTime.md#response">response</a></td>
            <td>Get the device full date and time with <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a> flag.</td>
        </tr>
        <tr>
            <td><code>0x08</code></td>
            <td><code>SetDateTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/SetDateTime.md#request">request</a> / <a href="../../mtx1/commands/SetDateTime.md#response">response</a></td>
            <td>Set the device full date and time with <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a> flag.</td>
        </tr>
        <tr>
            <td><code>0x09</code></td>
            <td><code>SetAccessKey</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetAccessKey.md#request">request</a> / <a href="../../mtx1/commands/SetAccessKey.md#response">response</a></td>
            <td>Set the device access key.</td>
        </tr>
        <tr>
            <td><code>0x11</code></td>
            <td><code>SetSeasonProfile</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetSeasonProfile.md#request">request</a> / <a href="../../mtx1/commands/SetSeasonProfile.md#response">response</a></td>
            <td>Set season profile information for the given tariff table.</td>
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
            <td>Get current energy <code>A+, R+, R-</code> for tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x10</code></td>
            <td><code>SetDayProfile</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetDayProfile.md#request">request</a> / <a href="../../mtx1/commands/SetDayProfile.md#response">response</a></td>
            <td>Set day profile information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x12</code></td>
            <td><code>SetSpecialDay</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetSpecialDay.md#request">request</a> / <a href="../../mtx1/commands/SetSpecialDay.md#response">response</a></td>
            <td>Set special day information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x13</code></td>
            <td><code>ActivateRatePlan</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/ActivateRatePlan.md#request">request</a> / <a href="../../mtx1/commands/ActivateRatePlan.md#response">response</a></td>
            <td>Provide the date and parameters of tariff plan activation.</td>
        </tr>
        <tr>
            <td><code>0x14</code></td>
            <td><code>PrepareRatePlan</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/PrepareRatePlan.md#request">request</a> / <a href="../../mtx1/commands/PrepareRatePlan.md#response">response</a></td>
            <td>Prepare device for rate plan application.</td>
        </tr>
        <tr>
            <td><code>0x15</code></td>
            <td><code>GetHalfHourDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemand.md#request">request</a> / <a href="./GetHalfHourDemand.md#response">response</a></td>
            <td>Get the active energy (<code>A+</code>) in half hours by date.</td>
        </tr>
        <td><code>0x016</code></td>
            <td><code>GetDayDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayDemand.md#request">request</a> / <a href="./GetDayDemand.md#response">response</a></td>
            <td>Get the daily active energy (<code>A+, R+, R-</code>) by default or selected energy type for all tariffs (<code>T1</code>-<code>T4</code>) for date.</td>
        </tr>
        <tr>
            <td><code>0x17</code></td>
            <td><code>GetMonthDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetMonthDemand.md#request">request</a> / <a href="./GetMonthDemand.md#response">response</a></td>
            <td>Get the monthly active energy (<code>A+</code>, <code>R+</code>, <code>R-</code>) for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x18</code></td>
            <td><code>TurnRelayOn</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/TurnRelayOn.md#request">request</a> / <a href="../../mtx1/commands/TurnRelayOn.md#response">response</a></td>
            <td>Turn the device relay on.</td>
        </tr>
        <tr>
            <td><code>0x19</code></td>
            <td><code>TurnRelayOff</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/TurnRelayOff.md#request">request</a> / <a href="../../mtx1/commands/TurnRelayOff.md#response">response</a></td>
            <td>Turn the device relay off.</td>
        </tr>
        <tr>
            <td><code>0x1c</code></td>
            <td><code>SetCorrectTime</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetCorrectTime.md#request">request</a> / <a href="../../mtx1/commands/SetCorrectTime.md#response">response</a></td>
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
            <td><a href="../../mtx1/commands/GetVersion.md#request">request</a> / <a href="../../mtx1/commands/GetVersion.md#response">response</a></td>
            <td>Get device version information.</td>
        </tr>
        <tr>
            <td><code>0x29</code></td>
            <td><code>GetSaldo</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetSaldo.md#request">request</a> / <a href="../../mtx1/commands/GetSaldo.md#response">response</a></td>
            <td>Get device current saldo information.</td>
        </tr>
        <tr>
            <td><code>0x2a</code></td>
            <td><code>SetSaldo</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetSaldo.md#request">request</a> / <a href="../../mtx1/commands/SetSaldo.md#response">response</a></td>
            <td>Set device current saldo information.</td>
        </tr>
        <tr>
            <td><code>0x2c</code></td>
            <td><code>GetRatePlanInfo</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetRatePlanInfo.md#request">request</a> / <a href="../../mtx1/commands/GetRatePlanInfo.md#response">response</a></td>
            <td>Get device rate plan information.</td>
        </tr>
        <tr>
            <td><code>0x2e</code></td>
            <td><code>GetSaldoParameters</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetSaldoParameters.md#request">request</a> / <a href="../../mtx1/commands/GetSaldoParameters.md#response">response</a></td>
            <td>Get device current saldo parameters information.</td>
        </tr>
        <tr>
            <td><code>0x2f</code></td>
            <td><code>SetSaldoParameters</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/SetSaldoParameters.md#request">request</a> / <a href="../../mtx1/commands/SetSaldoParameters.md#response">response</a></td>
            <td>Set device current saldo parameters information.</td>
        </tr>
        <tr>
            <td><code>0x31</code></td>
            <td><code>GetDayMaxDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayMaxDemand.md#request">request</a> / <a href="./GetDayMaxDemand.md#response">response</a></td>
            <td>Get the maximum daily power (<code>A+R+</code>, <code>R+</code>, <code>A+R-</code>) for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x32</code></td>
            <td><code>GetMonthMaxDemand</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetMonthMaxDemand.md#request">request</a> / <a href="./GetMonthMaxDemand.md#response">response</a></td>
            <td>Get the maximum monthly power (<code>A+R+</code>, <code>R+</code>, <code>A+R-</code>) for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x33</code></td>
            <td><code>GetEvents</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetEvents.md#request">request</a> / <a href="../../mtx1/commands/GetEvents.md#response">response</a></td>
            <td>Get events.</td>
        </tr>
        <tr>
            <td><code>0x34</code></td>
            <td><code>GetEventsCounters</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetEventsCounters.md#request">request</a> / <a href="../../mtx1/commands/GetEventsCounters.md#response">response</a></td>
            <td>Get events counters.</td>
        </tr>
        <tr>
            <td><code>0x35</code></td>
            <td><code>ResetPowerMaxDay</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/ResetPowerMaxDay.md#request">request</a> / <a href="../../mtx1/commands/ResetPowerMaxDay.md#response">response</a></td>
            <td>Reset daily max power.</td>
        </tr>
        <tr>
            <td><code>0x36</code></td>
            <td><code>ResetPowerMaxMonth</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/commands/ResetPowerMaxMonth.md#request">request</a> / <a href="../../mtx1/commands/ResetPowerMaxMonth.md#response">response</a></td>
            <td>Reset for monthly max power.</td>
        </tr>
        <tr>
            <td><code>0x39</code></td>
            <td><code>GetCurrentStatusMeter</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetCurrentStatusMeter.md#request">request</a> / <a href="./GetCurrentStatusMeter.md#response">response</a></td>
            <td>Get current meter status.</td>
        </tr>
        <tr>
            <td><code>0x3a</code></td>
            <td><code>GetExtendedCurrentValues</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetExtendedCurrentValues.md#request">request</a> / <a href="./GetExtendedCurrentValues.md#response">response</a></td>
            <td>Get the temperature, supply frequency, etc.</td>
        </tr>
        <tr>
            <td><code>0x3b</code></td>
            <td><code>GetDayProfile</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetDayProfile.md#request">request</a> / <a href="../../mtx1/commands/GetDayProfile.md#response">response</a></td>
            <td>Get day profile information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x3c</code></td>
            <td><code>GetSeasonProfile</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetSeasonProfile.md#request">request</a> / <a href="../../mtx1/commands/GetSeasonProfile.md#response">response</a></td>
            <td>Get season profile information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x3d</code></td>
            <td><code>GetSpecialDay</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetSpecialDay.md#request">request</a> / <a href="../../mtx1/commands/GetSpecialDay.md#response">response</a></td>
            <td>Get special day information for the given tariff table.</td>
        </tr>
        <tr>
            <td><code>0x3e</code></td>
            <td><code>GetCorrectTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetCorrectTime.md#request">request</a> / <a href="../../mtx1/commands/GetCorrectTime.md#response">response</a></td>
            <td>Get <a href="https://en.wikipedia.org/wiki/Daylight_saving_time">DST</a>/Standard time transition options.</td>
        </tr>
        <tr>
            <td><code>0x3f</code></td>
            <td><code>GetOperatorParametersExtended</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetOperatorParametersExtended.md#request">request</a> / <a href="./GetOperatorParametersExtended.md#response">response</a></td>
            <td>Get extended device operator parameters.</td>
        </tr>
        <tr>
            <td><code>0x40</code></td>
            <td><code>SetOperatorParametersExtended</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetOperatorParametersExtended.md#request">request</a> / <a href="./SetOperatorParametersExtended.md#response">response</a></td>
            <td>Set extended device operator parameters.</td>
        </tr>
        <tr>
            <td><code>0x45</code></td>
            <td><code>SetOperatorParametersExtended2</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetOperatorParametersExtended2.md#request">request</a> / <a href="./SetOperatorParametersExtended2.md#response">response</a></td>
            <td>Set extended device operator parameters <code>2</code>.</td>
        </tr>
        <tr>
            <td><code>0x47</code></td>
            <td><code>GetOperatorParametersExtended2</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetOperatorParametersExtended2.md#request">request</a> / <a href="./GetOperatorParametersExtended2.md#response">response</a></td>
            <td>Get extended device operator parameters <code>2</code>.</td>
        </tr>
        <tr>
            <td><code>0x48</code></td>
            <td><code>GetHalfHourDemandVari</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandVari.md#request">request</a> / <a href="./GetHalfHourDemandVari.md#response">response</a></td>
            <td>Get the reactive energy (<code>`A+R+`</code>) in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x49</code></td>
            <td><code>GetHalfHourDemandVare</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandVare.md#request">request</a> / <a href="./GetHalfHourDemandVare.md#response">response</a></td>
            <td>Get the reactive energy (<code>`A+R-`</code>) in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x4e</code></td>
            <td><code>GetEnergyExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEnergyExport.md#request">request</a> / <a href="./GetEnergyExport.md#response">response</a></td>
            <td>Get current energy <code>A-, R+, R-</code> for tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x4f</code></td>
            <td><code>GetDayDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayDemandExport.md#request">request</a> / <a href="./GetDayDemandExport.md#response">response</a></td>
            <td>Get daily energy <code>A-, R+, R-</code> for all tariffs (<code>T1</code>-<code>T4</code>) for date.</td>
        </tr>
        <tr>
            <td><code>0x50</code></td>
            <td><code>GetEnergyExportDayPrevious</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetEnergyExportDayPrevious.md#request">request</a> / <a href="./GetEnergyExportDayPrevious.md#response">response</a></td>
            <td>Get the previous day active energy <code>A-, R+, R-</code> for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x52</code></td>
            <td><code>GetMonthDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetMonthDemandExport.md#request">request</a> / <a href="./GetMonthDemandExport.md#response">response</a></td>
            <td>Get the monthly energies (<code>A-</code>, <code>A-R+</code>, <code>A-R-</code>) for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x53</code></td>
            <td><code>GetHalfHourDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandExport.md#request">request</a> / <a href="./GetHalfHourDemandExport.md#response">response</a></td>
            <td>Get the active energy <code>A-</code> (<code>II</code> - <code>III</code> quadrant) in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x54</code></td>
            <td><code>GetHalfHourDemandVariExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandVariExport.md#request">request</a> / <a href="./GetHalfHourDemandVariExport.md#response">response</a></td>
            <td>Get the reactive energy <code>`A-R+`</code> in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x55</code></td>
            <td><code>GetHalfHourDemandVareExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandVareExport.md#request">request</a> / <a href="./GetHalfHourDemandVareExport.md#response">response</a></td>
            <td>Get the reactive energy <code>`A-R-`</code> in half hours by date.</td>
        </tr>
        <tr>
            <td><code>0x56</code></td>
            <td><code>GetCriticalEvent</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetCriticalEvent.md#request">request</a> / <a href="./GetCriticalEvent.md#response">response</a></td>
            <td>Get device critical events.</td>
        </tr>
        <tr>
            <td><code>0x58</code></td>
            <td><code>GetDayMaxDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetDayMaxDemandExport.md#request">request</a> / <a href="./GetDayMaxDemandExport.md#response">response</a></td>
            <td>Get the maximum daily power (<code>II</code>-<code>III</code> quadrant) for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x59</code></td>
            <td><code>GetMonthMaxDemandExport</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetMonthMaxDemandExport.md#request">request</a> / <a href="./GetMonthMaxDemandExport.md#response">response</a></td>
            <td>Get the maximum monthly power (<code>II</code>-<code>III</code> quadrant) for all tariffs (<code>T1</code>-<code>T4</code>).</td>
        </tr>
        <tr>
            <td><code>0x5a</code></td>
            <td><code>GetHalfHourDemandChannel</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetHalfHourDemandChannel.md#request">request</a> / <a href="./GetHalfHourDemandChannel.md#response">response</a></td>
            <td>Get half hours for the selected channel by date.</td>
        </tr>
        <tr>
            <td><code>0x5c</code></td>
            <td><code>SetCorrectDateTime</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/SetCorrectDateTime.md#request">request</a> / <a href="../../mtx1/commands/SetCorrectDateTime.md#response">response</a></td>
            <td>Incremental device time correction (for a given number of seconds).</td>
        </tr>
        <tr>
            <td><code>0x5d</code></td>
            <td><code>SetDisplayParam</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetDisplayParam.md#request">request</a> / <a href="../../mtx1/commands/SetDisplayParam.md#response">response</a></td>
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
            <td><a href="../../mtx1/commands/SetSpecialOperation.md#request">request</a> / <a href="../../mtx1/commands/SetSpecialOperation.md#response">response</a></td>
            <td>Set special parameters.</td>
        </tr>
        <tr>
            <td><code>0x6d</code></td>
            <td><code>GetMagneticFieldThreshold</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetMagneticFieldThreshold.md#request">request</a> / <a href="../../mtx1/commands/GetMagneticFieldThreshold.md#response">response</a></td>
            <td>Get parameters related to magnetic field detection.</td>
        </tr>
        <tr>
            <td><code>0x6f</code></td>
            <td><code>GetHalfHourEnergies</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetHalfHourEnergies.md#request">request</a> / <a href="../../mtx1/commands/GetHalfHourEnergies.md#response">response</a></td>
            <td>Get energy with <code>30</code>-minute accumulation period by selected energy type for date.</td>
        </tr>
        <tr>
            <td><code>0x71</code></td>
            <td><code>GetOperatorParametersExtended3</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/GetOperatorParametersExtended3.md#request">request</a> / <a href="../../mtx1/commands/GetOperatorParametersExtended3.md#response">response</a></td>
            <td>Get extended device operator parameters <code>3</code>.</td>
        </tr>
        <tr>
            <td><code>0x72</code></td>
            <td><code>SetOperatorParametersExtended3</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="../../mtx1/SetOperatorParametersExtended3.md#request">request</a> / <a href="../../mtx1/commands/SetOperatorParametersExtended3.md#response">response</a></td>
            <td>Set extended device operator parameters <code>3</code>.</td>
        </tr>
        <tr>
            <td><code>0x74</code></td>
            <td><code>SetOperatorParametersExtended4</code></td>
            <td><strong><code>READ_WRITE</code></strong></td>
            <td><a href="./SetOperatorParametersExtended4.md#request">request</a> / <a href="./SetOperatorParametersExtended4.md#response">response</a></td>
            <td>Set extended device operator parameters <code>4</code>.</td>
        </tr>
        <tr>
            <td><code>0x75</code></td>
            <td><code>GetOperatorParametersExtended4</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="./GetOperatorParametersExtended4.md#request">request</a> / <a href="./GetOperatorParametersExtended4.md#response">response</a></td>
            <td>Get extended device operator parameters <code>4</code>.</td>
        </tr>
        <tr>
            <td><code>0x76</code></td>
            <td><code>GetDemand</code></td>
            <td><strong><code>READ_ONLY</code></strong></td>
            <td><a href="./GetDemand.md#request">request</a> / <a href="./GetDemand.md#response">response</a></td>
            <td>Get the measurement data by selected type for date.</td>
        </tr>
        <tr>
            <td><code>0x7a</code></td>
            <td><code>GetMeterInfo</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/GetMeterInfo.md#request">request</a> / <a href="../../mtx1/commands/GetMeterInfo.md#response">response</a></td>
            <td>Get meter info.</td>
        </tr>
        <tr>
            <td><code>0xfe</code></td>
            <td><code>ErrorResponse</code></td>
            <td><code>READ_ONLY</code></td>
            <td><a href="../../mtx1/commands/ErrorResponse.md#response">response</a></td>
            <td>Provide info for the failed downlink command.</td>
        </tr>
    </tbody>
</table>


**Note**

All number fields in the commands are transmitted in big-endian format.
