# FGT_Auditor

This software can be used to audit Fortigate's configuration file.
For now, you can only use the software with -l <folder> option where is located all your config file (only 1 file can be added to this folder).

Syntax : python3 FGT_Auditor -l ../config_folder
  
Steps :
  - Creating of a folder named "reports" inside the current directory where the software was run.
  - Read all file in the specified directory
  - Export all configuration in CSV file
  - Read CSV file and audit them to get an output with special warning configured in the script.
  

The output is like :

``` [*] Firewall-1 folder is located at : FGT_Auditor/reports/Firewall-1"
[*] Firewall-1 : Network interfaces exported to CSV done."
##############################
[!] VULNERABLE INTERFACE [!]
dmz                              ping https http    192.168.0.1 255.255.255.0 
wan2                                        https    192.168.1.1 255.255.255.0 
lan                          ping https ssh snmp     192.168.2.254 255.255.255.0 
##############################
[*] Firewall-1 : IPSEC Phase1 exported to CSV done. [*]
IPSEC are well configured
[*] Firewall-1 : Firewall policies exported to CSV done. [*]
[!] SRC [!] Policy ID   1 contains "all" on its source address [!] UUID :  xxxx-xxxx-xxxx-xxxx
[!] SRC [!] Policy ID   2 contains "all" on its source address [!] UUID :  xxxx-xxxx-xxxx-xxxx
[!] SRC [!] Policy ID   4 contains "all" on its source address [!] UUID :  xxxx-xxxx-xxxx-xxxx
[!] DST [!] Policy ID   1 contains "all" on its destination address [!] UUID :  xxxx-xxxx-xxxx-xxxx
[!] DST [!] Policy ID   5 contains "all" on its destination address [!] UUID :  xxxx-xxxx-xxxx-xxxx
[!] DST [!] Policy ID   8 contains "all" on its destination address [!] UUID :  xxxx-xxxx-xxxx-xxxx
[*] Firewall-1 : Static routes exported to CSV done. [*]
[*] Firewall-1 : Services exported to CSV done. [*]
[*] Firewall-1 : Services Groups exported to CSV done. [*]
[*] Firewall-1 : SNMP communities exported to CSV done. [*]
[*] Firewall-1 : SSL settings exported to CSV done. [*]
[*] Firewall-1 : SSL portals exported to CSV done. [*]

[!] SSL VPN is active on interface  wan2
##############################
       servercert      tunnel-ip-pools         tunnel-ipv6-pools  port source-interface source-address source-address6 default-portal
 Fortinet_Factory  SSLVPN_TUNNEL_ADDR1  SSLVPN_TUNNEL_IPv6_ADDR1   443             wan2            all             all     web-access
##############################

[*] Firewall-1 : Virtual IP exported to CSV done. [*]
##############################

[!] VIRTUAL IP IS CONFIGURED [!]
                     id                                  uuid           extip        extintf portforward         mappedip  extport  mappedport         comment  color protocol
             Web-Server  				  xxxx-xxxx-xxxx-xxxx         1.1.1.1          wan1      enable     192.168.0.2   83.0      83.0             NaN    NaN      NaN
##############################
```
