This is based on https://share.zabbix.com/storage-devices/freenas-snmp-w-zfs-stats

It has more graphs and triggers. It uses the OID as zabbix was having issues parsing the MIB.

Note: You might get erros if you don't fix the MIB. See bug here:
https://forums.freenas.org/index.php?threads/freenas-11-1-snmp-index-out-of-range.62732/


1) Import the following templates if they are not already
https://share.zabbix.com/official-templates/snmp-devices/snmp-interfaces-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-processors-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-generic

2) The FREENAS-MIB.txt will also need to be uploaded to your Zabbix Server. The MIB can be downloaded from your FreeNAS server and is located in /usr/local/share/snmp/mibs/.

3) Import the template

4) Add the host, include the macro {$SNMPCOMMUNITY}

5) Wait

Memory should be pretty quick while the zpools might take a while.