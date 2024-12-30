Hostname R1
service password-encryption
security passwords min-length 10
login block-for 180 attempts 4 within 120
enable secret class
ipv6 unicast-routing
username miki secret cisco
no ip domain-lookup
ip domain-name pxl.be
interface GigabitEthernet0/0/0
description Verbinding naar Switch1
ip address 192.168.20.1 255.255.255.0
ipv6 address FE80::1 link-local
ipv6 address 2001:DB8:2::1/64
interface GigabitEthernet0/0/1
description Verbinding naar Switch2
ip address 192.168.10.1 255.255.255.0
no shut
ipv6 address FE80::2 link-local
ipv6 address 2001:DB8:1::1/64
no shut
line con 0
password pxl
login
line vty 0 4
exec-timeout 6 
login local
transport input ssh
crypto key generate rsa general-keys modulus 2048
exit
exit
copy running-config startup-config