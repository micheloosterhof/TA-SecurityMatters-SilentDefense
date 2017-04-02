*********************************************
*
* Add-On: SecurityMatters SilentDefense Add-On for Splunk
* Current Version: 0.1
* Last Modified: Apr 2017
* Splunk Version: 6.5
* Author: Michel Oosterhof
*
*********************************************


**** To get SilentDefense log data into Splunk ****

1. Configure SilentDefense to send alerts to Splunk using the following template:

=======
{"time":"{tsFormattedRFC5424}", "valertId":"{alertId}", "sensorName":"{sensorName}", "engineName":"{engineName}", "dstNetworkName":"{dstNetworkName}", "dstHostName":"{dstHostName}", l2Proto":"{l2Proto}", "l3Proto":"{l3Proto}", "l4Proto":"{l4Proto}", "l7Proto":"{l7Proto}", "srcMac":"{srcMac}", "srcIp":"{srcIp}", "srcPort":"{srcPort}", "dstMac":"{dstMac}", "dstIp":"{dstIp}", "vlan":"{vlan}", "dstPort":"{dstPort}", "severity":"{severity}", "status":"{status}", "profId":"{profId}", "profModName":"{profModName}", "upDataLength":"{upDataLength}", "downDataLength":"{downDataLength}", "pcapSha1":"{pcapSha1}", "typeId":"{typeId}", "name":"{name}", "desc":"{desc}", "streamDir":"{streamDir}", "fieldPath":"{fieldPath}", "fieldVal":"{fieldVal}", "expFieldVals":"{expFieldVals}", "feaState":"{feaState}", "feaAlertCount":"{feaAlertCount}", "feaAlertDetailCount":"{feaAlertDetailCount}", "feaStartMillisec":"{feaStartMillisec}", "feaStartFormatted":"{feaStartFormatted}", "feaDurationSec":"{feaDurationSec}"} 
=======

2. Configure Splunk to extract SilentDefense events

Before using this Add-on, you have to config a data input, and give the input data
a default sourcetype of "securitymatters:silentdefense:syslog"

Splunk will automatically rename the sourcetype based on the data that's sent.


**** sourcetypes ****

        securitymatters:silentdefense:syslog
		* only used for initial data input

        securitymatters:silentdefense:alert:syslog
        securitymatters:silentdefense:asset:syslog
        securitymatters:silentdefense:flow:syslog
        securitymatters:silentdefense:health:syslog

**** eventtypes ****

        securitymatters-silentdefense-alert
        securitymatters-silentdefense-asset
        securitymatters-silentdefense-flow
        securitymatters-silentdefense-health


**** CIM mappings ****

	Change Analysis
	Intrusion Detection
	Network Traffic


**** Release Notes ****

v0.1: Apr 2017
        - Initial release, only works for alerts at this point in time. Plans to extend to other sourcetypes
