This is based on https://share.zabbix.com/storage-devices/freenas-snmp-w-zfs-stats


1) Import the following templates if they are not already
https://share.zabbix.com/official-templates/snmp-devices/snmp-interfaces-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-processors-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-generic

2) Import the template

3) Add the host, include the macro {$SNMPCOMMUNITY}

4) Wait

Memory should be pretty quick while the zpools might take a while.