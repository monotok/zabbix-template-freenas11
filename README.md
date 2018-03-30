This is based on https://share.zabbix.com/storage-devices/freenas-snmp-w-zfs-stats

It has more graphs and triggers. It uses the OID as zabbix was having issues parsing the MIB.

Note: You might get erros if you don't fix the MIB. See bug here:
https://forums.freenas.org/index.php?threads/freenas-11-1-snmp-index-out-of-range.62732/

Please Note: For ZVols, ZPools and Datasets the data is multiplied by 4096 under PreProcessing. This is the AllocationUnits. All of mine were 4096 so decided this is neater. Obviously this can be changed if required, you can get his data from an SNMP Walk. This could be done automatically by creating a item prototype of allocationUnits, another to get the data in units and then another item prototype to to calculate the value in bytes. This would instead of 14 item prototypes; there would be 42. If anyone knows of a better way then please let me know.

Eg: snmpwalk -v 2c -c public 192.168.1.50 FREENAS-MIB::zvolAllocationUnits
snmpwalk -v 2c -c public 192.168.1.50 FREENAS-MIB::zpoolAllocationUnits
snmpwalk -v 2c -c public 192.168.1.50 FREENAS-MIB::datasetAllocationUnits



1) Import the following templates if they are not already
https://share.zabbix.com/official-templates/snmp-devices/snmp-interfaces-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-processors-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-generic

2) The FREENAS-MIB.txt will also need to be uploaded to your Zabbix Server. The MIB can be downloaded from your FreeNAS server and is located in /usr/local/share/snmp/mibs/.

3) Import the template

4) Add the host, include the macro {$SNMPCOMMUNITY}

5) Wait

Memory should be pretty quick while the zpools might take a while.