# TP_SDN
Configuration du Routeur et des proxmox


Configuration du routeur : 

2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

    link/ether 00:0c:29:7e:99:ed brd ff:ff:ff:ff:ff:ff
    
    altname enp2s1
    
    inet 1.1.1.1/24 scope global ens33
    
       valid_lft forever preferred_lft forever
       

    
3: ens36: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

    link/ether 00:0c:29:7e:99:f7 brd ff:ff:ff:ff:ff:ff
    
    altname enp2s4
    
    inet 192.168.75.31/24 brd 192.168.75.255 scope global noprefixroute ens36
    
       valid_lft forever preferred_lft forever
       
    inet6 fe80::20c:29ff:fe7e:99f7/64 scope link noprefixroute 
    
       valid_lft forever preferred_lft forever
       


Configuration de Firewalld : 
```
internal (active)
  target: default
  icmp-block-inversion: no
  interfaces: ens33
  sources: 
  services: dhcpv6-client mdns samba-client ssh
  ports: 
  protocols: 
  forward: yes
  masquerade: no
  forward-ports: 
  source-ports: 
  icmp-blocks: 
  rich rules: 

external (active)
  target: default
  icmp-block-inversion: no
  interfaces: ens36
  sources: 
  services: ssh
  ports: 
  protocols: 
  forward: yes
  masquerade: yes
  forward-ports: 
  source-ports: 
  icmp-blocks: 
  rich rules:
```  
