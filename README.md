# SecurityMatters SilentDefense Add-On for Splunk

* Current Version: 0.2
* Last Modified: Apr 2017
* Splunk Version: 6.5
* Author: Michel Oosterhof

## Installation and configuration


1. Configure Splunk to receive SilentDefense events

Before using this Add-on, you have to add a data input, and assign
the input data a default sourcetype of
"securitymatters:silentdefense:syslog"

1. Configure SilentDefense to send alerts to Splunk using the following template:

```
"time":"{tsFormattedRFC5424}", "valertId":"{alertId}", "sensorName":"{sensorName}", "engineName":"{engineName}", "dstNetworkName":"{dstNetworkName}", "dstHostName":"{dstHostName}", l2Proto":"{l2Proto}", "l3Proto":"{l3Proto}", "l4Proto":"{l4Proto}", "l7Proto":"{l7Proto}", "srcMac":"{srcMac}", "srcIp":"{srcIp}", "srcPort":"{srcPort}", "dstMac":"{dstMac}", "dstIp":"{dstIp}", "vlan":"{vlan}", "dstPort":"{dstPort}", "severity":"{severity}", "status":"{status}", "profId":"{profId}", "profModName":"{profModName}", "upDataLength":"{upDataLength}", "downDataLength":"{downDataLength}", "pcapSha1":"{pcapSha1}", "typeId":"{typeId}", "name":"{name}", "desc":"{desc}", "streamDir":"{streamDir}", "fieldPath":"{fieldPath}", "fieldVal":"{fieldVal}", "expFieldVals":"{expFieldVals}", "feaState":"{feaState}", "feaAlertCount":"{feaAlertCount}", "feaAlertDetailCount":"{feaAlertDetailCount}", "feaStartMillisec":"{feaStartMillisec}", "feaStartFormatted":"{feaStartFormatted}", "feaDurationSec":"{feaDurationSec}"} 
```

## Reference

### Sourcetypes

Input data should be of sourcetype  ```securitymatters:silentdefense:syslog```
The add-on will rewrite the sourcetype based on received data to one of the following:

* ```securitymatters:silentdefense:alert:syslog```
* ```securitymatters:silentdefense:asset:syslog```
* ```securitymatters:silentdefense:flow:syslog```
* ```securitymatters:silentdefense:link:syslog```
* ```securitymatters:silentdefense:health:syslog```

### Eventtypes

The data will have the following event types, with a 1-1 mapping of sourcetype to eventtype

* ```securitymatters-silentdefense-alert```
* ```securitymatters-silentdefense-asset```
* ```securitymatters-silentdefense-flow```
* ```securitymatters-silentdefense-link```
* ```securitymatters-silentdefense-health```

### Data Models
  
* Alert data is sent to the Network Intrusion Detection Data Model
* Flow and Link data is sent to the Network Traffic Data Model

## Release Notes

v0.2: 5 April 2017
        - Add support for flow data, link data, health data and asset data

v0.1: Apr 2017
        - Initial release, only works for alerts at this point in time. Plans to extend to other sourcetypes

