
@C1

config t
vlan 23
name FUELSAVE.COM
Interface vlan 23
 desc FUELSAVE.COM
 no shut
 ip add 10.0.2.1 255.255.254.0
ip dhcp excluded-add 10.0.2.1 10.0.2.100
ip dhcp pool FUELSAVE.COM
 network  10.0.2.0 255.255.254.0
 default-router 10.0.2.1
 domain-name FUELSAVE.COM
 do sh run | sec dhcp

@c2
config t
int e1/0
no shut
switchport mode access
switchport access vlan 23
do sh vlan brief

@s2
config t
int e1/0
no shut
ip add dhcp
do bp
