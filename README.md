This is based on https://share.zabbix.com/storage-devices/freenas-snmp-w-zfs-stats

It has more graphs and triggers. It uses the OID as zabbix was having issues parsing the MIB.

Note: You might get erros if you don't fix the MIB. See bug here:
https://forums.freenas.org/index.php?threads/freenas-11-1-snmp-index-out-of-range.62732/

Please Note: For ZVols and Datasets the data is multiplied now by AllocationUnit provided via SNMP for each of them. 
Due to very inconsistent MIB data, some of the ZVol, Zpool an Dataset data is reported in units (AllocationUnits) and some of it is reported in Bytes.
I.E. Used space per dataset/zvol is reported in bytes, but available space is reported in allocation units.
This is not the case for Zpools! 
Who decided this is a good idea, I don't know. 

Additionally, I calculate some of the IO/s and read/write data as the one provided via MIB is only instantaneous (as within last second).
Ops for ZIL, I don't even think they work. I have ZIL on one of the devices but see no data for it. They also are only instantenous for last 1,5 or 10 seconds.



Useful info below:

1) Import the following templates if they are not already
https://share.zabbix.com/official-templates/snmp-devices/snmp-interfaces-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-processors-discovery
https://share.zabbix.com/official-templates/snmp-devices/snmp-generic

2) The FREENAS-MIB.txt will also need to be uploaded to your Zabbix Server. The MIB can be downloaded from your FreeNAS server and is located in /usr/local/share/snmp/mibs/.

3) Import the template

4) Add the host, include the macro {$SNMPCOMMUNITY}

5) Wait

Memory should be pretty quick while the zpools might take a while.
