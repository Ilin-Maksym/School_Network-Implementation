# School network

## Description
  This project uses Cisco Packet Tracer to simulate a small school network. It was built as a learning exercise to practice designing, configuring, and securing a network with multiple devices and limited resources.

## Network Diagram
![Network Diagram](image/Network.png)

## Network Segments
The network can be separated on three different segments:
  Light blue, school network:
  ![School Network](image/School.png)
  Orange, internet:
  ![School Network](image/Internet.png)
  Purple and pink, routers:
  ![School Network](image/Routers.png)

## Network Components
| Component Type | Model                                      | Quantity |
|----------------|--------------------------------------------|----------|
| Switch         | Cisco 2960                                 | 6        |
| L3 Switch      | Cisco 3650-24PS                            | 1        |
| Router         | Cisco PT-Empty(1CGE/PT-ROUTER-NM-1S_ports) | 4        |
| PC             | Generic PC                                 | 7        |
| Laptop         | Generic Laptop                             | 2        |
| Server         | Cisco Server                               | 3        |
| Access point   | AccessPoint-PT                             | 1        |

## IP Addressing Scheme
| Device                   | Interface      | IP Address      | Subnet Mask     | Default Gateway | NAT     |
|--------------------------|----------------|-----------------|-----------------|-----------------|---------|
| Servers_SW:              |                |                 |                 |                 |         |
|   VLAN 1                 | Management     | 192.168.100.2   | 255.255.255.128 | 192.168.100.1   |         |
|   VLAN 10                | Range F0/1-2   | 192.168.0.0     | 255.255.255.0   | 192.168.0.1     |         |
|   Admin_Server           | F0/1           | 192.168.0.2     | 255.255.255.0   | 192.168.0.1     |         |
|   School_Server          | F0/2           | 192.168.0.3     | 255.255.255.0   | 192.168.0.1     |         |
|   L3_SW                  | G0/1           |                 |                 |                 |         |
| Floor-1_SW:              |                |                 |                 |                 |         |
|   VLAN 1                 | Management     | 192.168.100.3   | 255.255.255.128 | 192.168.100.1   |         |
|   VLAN 12                | F0/2           | 172.16.10.0     | 255.255.254.0   | 172.16.10.1     |         |
|   VLAN 13                | F0/1           | 172.16.20.0     | 255.255.252.0   | 172.16.20.1     |         |
|   Teacher 1              | F0/2           | DHCP            | 255.255.254.0   | 172.16.10.1     |         |
|   Student 1              | F0/2           | DHCP            | 255.255.252.0   | 172.16.20.1     |         |
|   L3_SW                  | G0/1           |                 |                 |                 |         |
| Floor-2_SW:              |                |                 |                 |                 |         |
|   VLAN 1                 | Management     | 192.168.100.4   | 255.255.255.128 | 192.168.100.1   |         |
|   VLAN 12                | F0/2           | 172.16.10.0     | 255.255.254.0   | 172.16.10.1     |         |
|   VLAN 13                | F0/1           | 172.16.20.0     | 255.255.252.0   | 172.16.20.1     |         |
|   Teacher 2              | F0/2           | DHCP            | 255.255.254.0   | 172.16.10.1     |         |
|   Student 2              | F0/1           | DHCP            | 255.255.252.0   | 172.16.20.1     |         |
|   L3_SW                  | G0/1           |                 |                 |                 |         |
| Admin_SW:                |                |                 |                 |                 |         |
|   VLAN 1                 | Management     | 192.168.100.5   | 255.255.255.128 | 192.168.100.1   |         |
|   VLAN 11                | Range F0/1-2   | 192.168.1.0     | 255.255.255.0   | 192.168.1.1     |         |
|   Admin 1                | F0/1           | DHCP            | 255.255.255.0   | 192.168.1.1     |         |
|   Admin 2                | F0/2           | DHCP            | 255.255.255.0   | 192.168.1.1     |         |
|   L3_SW                  | G0/1           |                 |                 |                 |         |
| WIFI_SW:                 |                |                 |                 |                 |         |
|   VLAN 1                 | Management     | 192.168.100.6   | 255.255.255.128 | 192.168.100.1   |         |
|   Guest                  | School_WIFI-AP | DHCP            | 255.255.252.0   | 172.16.100.1    |         |
|   School_WIFI-AP         | F0/1           |                 |                 |                 |         |
|   L3_SW                  | G0/1           |                 |                 |                 |         |
| L3_SW:                   |                |                 |                 |                 |         |
|   VLAN 1                 | Management     | 192.168.100.1   | 255.255.255.128 |                 |         |
|   VLAN 10                | Servers        | 192.168.0.1     | 255.255.255.0   |                 |         |
|   VLAN 11                | Admin          | 192.168.1.1     | 255.255.255.0   |                 |         |
|   VLAN 12                | Teachers       | 172.16.10.1     | 255.255.254.0   |                 |         |
|   VLAN 13                | Students       | 172.16.20.1     | 255.255.252.0   |                 |         |
|   VLAN 100               | WIFI           | 172.16.100.1    | 255.255.252.0   |                 |         |
|   Default_Router-Access  | G1/0/24        | 192.168.100.129 | 255.255.255.252 |                 |         |
|   Servers_SW             | G1/0/1         |                 |                 |                 |         |
|   Floor-1_SW             | G1/0/2         |                 |                 |                 |         |
|   Floor-2_SW             | G1/0/3         |                 |                 |                 |         |
|   Admin_SW               | G1/0/4         |                 |                 |                 |         |
|   WIFI_SW                | G1/0/5         |                 |                 |                 |         |
| Default_Router:          |                |                 |                 |                 |         |
|   School_LAN-Access      | G0/0           | 192.168.100.130 | 255.255.255.252 |                 | Inside  |
|   Internet               | G1/0           | 88.207.207.1    | 255.255.255.252 |                 | Outside |
| ISP1:                    |                |                 |                 |                 |         |
|   Default_Router-Access  | G0/0           | 88.207.207.2    | 255.255.255.252 |                 |         |
|   ISP2-Access            | S1/0           | 88.207.207.5    | 255.255.255.252 |                 |         |
| ISP2:                    |                |                 |                 |                 |         |
|   ISP1-Access            | S1/0           | 88.207.207.6    | 255.255.255.252 |                 |         |
|   Internet_Router-Access | G0/0           | 88.207.207.9    | 255.255.255.252 |                 |         |
| Internet:                |                |                 |                 |                 |         |
|   ISP2-Access            | G1/0           | 88.207.207.10   | 255.255.255.252 |                 | Outside |
|   VLAN 10                | G0/0.10        | 10.10.10.1      | 255.255.255.0   |                 | Inside  |
|   VLAN 20                | G0/0.20        | 20.20.20.1      | 255.255.255.0   |                 | Inside  |
|   Webhost                | G0/0           |                 |                 |                 |         |
| Webhost:                 |                |                 |                 |                 |         |
|   VLAN 10                | Range F0/1-2   | 10.10.10.0      | 255.255.255.0   | 10.10.10.1      |         |
|   VLAN 20                | F0/24          | 20.20.20.0      | 255.255.255.0   | 20.20.20.1      |         |
|   PC0                    | F0/1           | DHCP            | 255.255.255.0   | 10.10.10.1      |         |
|   Laptop                 | F0/2           | DHCP            | 255.255.255.0   | 10.10.10.1      |         |
|   Hoster                 | F0/24          | 20.20.20.2      | 255.255.255.0   | 20.20.20.1      |         |
|   Internet_Router        | G0/1           |                 |                 |                 |         |

## Configuration Details
### L3_SW
Switch> enable

Switch# conf t


Switch(config)# hostname L3_SW


L3_SW(config)# interface vlan 1

L3_SW(config-if)# description Management

L3_SW(config-if)# ip address 192.168.100.1 255.255.255.128

L3_SW(config-if)# no shutdown

L3_SW(config-if)# exit


L3_SW(config)# vlan 10

L3_SW(config-vlan)# name Servers

L3_SW(config-vlan)# exit


L3_SW(config)# vlan 11

L3_SW(config-vlan)# name Admin

L3_SW(config-vlan)# exit


L3_SW(config)# vlan 12

L3_SW(config-vlan)# name Teachers

L3_SW(config-vlan)# exit


L3_SW(config)# vlan 13

L3_SW(config-vlan)# name Students

L3_SW(config-vlan)# exit


L3_SW(config)# vlan 100

L3_SW(config-vlan)# name WIFI

L3_SW(config-vlan)# exit


L3_SW(config)# interface vlan 10

L3_SW(config-if)# description Servers

L3_SW(config-if)# ip address 192.168.0.1 255.255.255.0

L3_SW(config-if)# no shutdown

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 11

L3_SW(config-if)# description Admin

L3_SW(config-if)# ip address 192.168.1.1 255.255.255.0

L3_SW(config-if)# no shutdown

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 12

L3_SW(config-if)# description Teachers

L3_SW(config-if)# ip address 172.16.10.1 255.255.254.0

L3_SW(config-if)# no shutdown

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 13

L3_SW(config-if)# description Students

L3_SW(config-if)# ip address 172.16.20.1 255.255.252.0

L3_SW(config-if)# no shutdown

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 100

L3_SW(config-if)# description WIFI

L3_SW(config-if)# ip address 172.16.100.1 255.255.252.0

L3_SW(config-if)# no shutdown

L3_SW(config-if)# exit


L3_SW(config)# interface range G1/0/1-5

L3_SW(config-if-range)# switchport

L3_SW(config-if-range)# switchport mode trunk

L3_SW(config-if-range)# exit


L3_SW(config)# ip dhcp pool Admin

L3_SW(dhcp-config)# network 192.168.1.0 255.255.255.0

L3_SW(dhcp-config)# default-router 192.168.1.1

L3_SW(dhcp-config)# exit


L3_SW(config)# ip dhcp pool Teachers

L3_SW(dhcp-config)# network 172.16.10.0 255.255.254.0

L3_SW(dhcp-config)# default-router 172.16.10.1

L3_SW(dhcp-config)# exit


L3_SW(config)# ip dhcp pool Students

L3_SW(dhcp-config)# network 172.16.20.0 255.255.252.0

L3_SW(dhcp-config)# default-router 172.16.20.1

L3_SW(dhcp-config)# exit


L3_SW(config)# ip dhcp pool WIFI

L3_SW(dhcp-config)# network 172.16.100.0 255.255.252.0

L3_SW(dhcp-config)# default-router 172.16.100.1

L3_SW(dhcp-config)# exit


L3_SW(config)# router ospf 1

L3_SW(config-router)# network 192.168.100.128 0.0.0.3 area 0

L3_SW(config-router)# network 192.168.1.0 0.0.0.255 area 0

L3_SW(config-router)# network 172.16.10.0 0.0.1.255 area 0

L3_SW(config-router)# network 172.16.20.0 0.0.3.255 area 0

L3_SW(config-router)# exit


L3_SW(config)# ip access-list extended Connection_Rules

L3_SW(config-ext-nacl)# deny ip 192.168.1.0 0.0.0.255 host 192.168.0.3

L3_SW(config-ext-nacl)# deny ip 172.16.10.0 0.0.1.255 host 192.168.0.2

L3_SW(config-ext-nacl)# deny ip 172.16.20.0 0.0.3.255 host 192.168.0.2

L3_SW(config-ext-nacl)# deny ip 172.16.100.0 0.0.3.255 host 192.168.0.2

L3_SW(config-ext-nacl)# deny ip 172.16.100.0 0.0.3.255 host 192.168.0.3

L3_SW(config-ext-nacl)# deny ip 172.16.10.0 0.0.1.255 192.168.100.0 0.0.0.128

L3_SW(config-ext-nacl)# deny ip 172.16.20.0 0.0.3.255 192.168.100.0 0.0.0.128

L3_SW(config-ext-nacl)# deny ip 172.16.100.0 0.0.3.255 192.168.100.0 0.0.0.128

L3_SW(config-ext-nacl)# deny ip 192.168.0.0 0.0.0.255 192.168.100.0 0.0.0.128

L3_SW(config-ext-nacl)# permit ip any any

L3_SW(config-ext-nacl)# exit


L3_SW(config)# interface vlan 10

L3_SW(config-if)# ip access-group Connection_Rules in

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 11

L3_SW(config-if)# ip access-group Connection_Rules in

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 12

L3_SW(config-if)# ip access-group Connection_Rules in

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 13

L3_SW(config-if)# ip access-group Connection_Rules in

L3_SW(config-if)# exit


L3_SW(config)# interface vlan 100

L3_SW(config-if)# ip access-group Connection_Rules in

L3_SW(config-if)# exit


L3_SW(config)# ip routing


L3_SW(config)# ip route 0.0.0.0 0.0.0.0 192.168.100.130

L3_SW(config)# exit


L3_SW# copy running-config startup-config

L3_SW# exit

### Servers_SW
Switch> enable

Switch# conf t


Switch(config)# hostname Servers_SW


Servers_SW(config)# interface vlan 1

Servers_SW(config-if)# description Management

Servers_SW(config-if)# ip address 192.168.100.2 255.255.255.128

Servers_SW(config-if)# no shutdown

Servers_SW(config-if)# exit


Servers_SW(config)# vlan 10

Servers_SW(config-vlan)# name Servers

Servers_SW(config-vlan)# exit


Servers_SW(config)# interface range F0/1-2

Servers_SW(config-if-range)# switchport mode access

Servers_SW(config-if-range)# switchport access vlan 10

Servers_SW(config-if-range)# exit


Servers_SW(config)# interface G0/1

Servers_SW(config-if)# switchmode trunk

Servers_SW(config-if)# exit


Servers_SW(config)# exit


Servers_SW# copy running-config startup-config

Servers_SW# exit

### Floor-1_SW
Switch> enable

Switch# conf t


Switch(config)# hostname Floor-1_SW


Floor-1_SW(config)# interface vlan 1

Floor-1_SW(config-if)# description Management

Floor-1_SW(config-if)# ip address 192.168.100.3 255.255.255.128

Floor-1_SW(config-if)# no shutdown

Floor-1_SW(config-if)# exit


Floor-1_SW(config)# vlan 12

Floor-1_SW(config-vlan)# name Teachers

Floor-1_SW(config-vlan)# exit


Floor-1_SW(config)# vlan 13

Floor-1_SW(config-vlan)# name Students

Floor-1_SW(config-vlan)# exit


Floor-1_SW(config)# interface F0/1

Floor-1_SW(config-if)# switchport mode access

Floor-1_SW(config-if)# switchport access vlan 13

Floor-1_SW(config-if)# exit


Floor-1_SW(config)# interface F0/2

Floor-1_SW(config-if)# switchport mode access

Floor-1_SW(config-if)# switchport access vlan 12

Floor-1_SW(config-if)# exit


Floor-1_SW(config)# interface G0/1

Floor-1_SW(config-if)# switchmode trunk

Floor-1_SW(config-if)# exit


Floor-1_SW(config)# exit


Floor-1_SW# copy running-config startup-config

Floor-1_SW# exit

### Floor-2_SW
Switch> enable

Switch# conf t


Switch(config)# hostname Floor-2_SW


Floor-2_SW(config)# interface vlan 1

Floor-2_SW(config-if)# description Management

Floor-2_SW(config-if)# ip address 192.168.100.4 255.255.255.128

Floor-2_SW(config-if)# no shutdown

Floor-2_SW(config-if)# exit


Floor-2_SW(config)# vlan 12

Floor-2_SW(config-vlan)# name Teachers

Floor-2_SW(config-vlan)# exit


Floor-2_SW(config)# vlan 13

Floor-2_SW(config-vlan)# name Students

Floor-2_SW(config-vlan)# exit


Floor-2_SW(config)# interface F0/1

Floor-2_SW(config-if)# switchport mode access

Floor-2_SW(config-if)# switchport access vlan 13

Floor-2_SW(config-if)# exit


Floor-2_SW(config)# interface F0/2

Floor-2_SW(config-if)# switchport mode access

Floor-2_SW(config-if)# switchport access vlan 12

Floor-2_SW(config-if)# exit


Floor-2_SW(config)# interface G0/1

Floor-2_SW(config-if)# switchmode trunk

Floor-2_SW(config-if)# exit


Floor-2_SW(config)# exit


Floor-2_SW# copy running-config startup-config

Floor-2_SW# exit

### Admin_SW
Switch> enable

Switch# conf t


Switch(config)# hostname Admin_SW


Admin_SW(config)# interface vlan 1

Admin_SW(config-if)# description Management

Admin_SW(config-if)# ip address 192.168.100.5 255.255.255.128

Admin_SW(config-if)# no shutdown

Admin_SW(config-if)# exit


Admin_SW(config)# vlan 11

Admin_SW(config-vlan)# name Admin

Admin_SW(config-vlan)# exit


Admin_SW(config)# interface range F0/1-2

Admin_SW(config-if-range)# switchport mode access

Admin_SW(config-if-range)# switchport access vlan 11

Admin_SW(config-if-range)# exit


Admin_SW(config)# interface G0/1

Admin_SW(config-if)# switchmode trunk

Admin_SW(config-if)# exit


Admin_SW(config)# exit


Admin_SW# copy running-config startup-config

Admin_SW# exit

### WIFI_SW
Switch> enable

Switch# conf t


Switch(config)# hostname Servers_SW


WIFI_SW(config)# interface vlan 1

WIFI_SW(config-if)# description Management

WIFI_SW(config-if)# ip address 192.168.100.6 255.255.255.128

WIFI_SW(config-if)# no shutdown

WIFI_SW(config-if)# exit


WIFI_SW(config)# vlan 100

WIFI_SW(config-vlan)# name WIFI

WIFI_SW(config-vlan)# exit


WIFI_SW(config)# interface F0/1

WIFI_SW(config-if)# switchport mode access

WIFI_SW(config-if)# switchport access vlan 100

WIFI_SW(config-if)# exit


WIFI_SW(config)# interface G0/1

WIFI_SW(config-if)# switchmode trunk

WIFI_SW(config-if)# exit


WIFI_SW(config)# exit


WIFI_SW# copy running-config startup-config

WIFI_SW# exit

### Default_Router
Router> enable

Router# conf t


Router(config)# hostname Default_Router


Default_Router(config)# interface G0/0

Default_Router(config-if)# description School_LAN

Default_Router(config-if)# ip address 192.168.100.130 255.255.255.252

Default_Router(config-if)# ip nat inside

Default_Router(config-if)# no shutdown

Default_Router(config-if)# exit


Default_Router(config)# interface G1/0

Default_Router(config-if)# description Internet

Default_Router(config-if)# ip address 88.207.207.1 255.255.255.252

Default_Router(config-if)# ip nat outside

Default_Router(config-if)# no shutdown

Default_Router(config-if)# exit


Default_Router(config)# router ospf 1

Default_Router(config-router)# network 192.168.100.128 0.0.0.3 area 0

Default_Router(config-router)# network 88.207.207.0 0.0.0.3 area 0

Default_Router(config-router)# exit


Default_Router(config)# router ospf 2

Default_Router(config-router)# network 88.207.207.0 0.0.0.3 area 1

Default_Router(config-router)# network 192.168.100.128 0.0.0.3 area 1

Default_Router(config-router)# exit


Default_Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255

Default_Router(config)# access-list 1 permit 172.16.10.0 0.0.1.255

Default_Router(config)# access-list 1 permit 172.16.20.0 0.0.3.255

Default_Router(config)# access-list 1 permit 172.16.100.0 0.0.3.255


Default_Router(config)# ip nat inside source list 1 interface G1/0 overload


Default_Router(config)# exit


Default_Router# copy running-config startup-config

Default_Router# exit

### ISP 1
Router> enable

Router# conf t


Router(config)# hostname ISP1


ISP1(config)# interface G0/0

ISP1(config-if)# description Default_Router

ISP1(config-if)# ip address 88.207.207.2 255.255.255.252

ISP1(config-if)# no shutdown

ISP1(config-if)# exit


ISP1(config)# interface S1/0

ISP1(config-if)# description ISP2

ISP1(config-if)# ip address 88.207.207.5 255.255.255.252

ISP1(config-if)# clock rate 64000

ISP1(config-if)# no shutdown

ISP1(config-if)# exit


ISP1(config)# router ospf 1

ISP1(config-router)# network 88.207.207.0 0.0.0.3 area 1

ISP1(config-router)# redistribute rip subnets

ISP1(config-router)# exit


ISP1(config)# router rip

ISP1(config-router)# no auto-summary

ISP1(config-router)# version 2

ISP1(config-router)# network 88.207.207.4

ISP1(config-router)# redistribute ospf 1 metric 1

ISP1(config-router)# exit


ISP1(config)# exit


ISP1# copy running-config startup-config

ISP1# exit

### ISP 2
Router> enable

Router# conf t


Router(config)# hostname ISP2


ISP2(config)# interface G0/0

ISP2(config-if)# description Internet_Router

ISP2(config-if)# ip address 88.207.207.9 255.255.255.252

ISP2(config-if)# no shutdown

ISP2(config-if)# exit


ISP2(config)# interface S1/0

ISP2(config-if)# description ISP1

ISP2(config-if)# ip address 88.207.207.6 255.255.255.252

ISP2(config-if)# no shutdown

ISP2(config-if)# exit


ISP2(config)# router ospf 1

ISP2(config-router)# network 88.207.207.8 0.0.0.3 area 1

ISP2(config-router)# redistribute rip subnets

ISP2(config-router)# exit


ISP2(config)# router rip

ISP2(config-router)# no auto-summary

ISP2(config-router)# version 2

ISP2(config-router)# network 88.207.207.4

ISP2(config-router)# redistribute ospf 1 metric 1

ISP2(config-router)# exit


ISP2(config)# exit


ISP2# copy running-config startup-config

ISP2# exit

### Internet_Router
Router> enable

Router# conf t


Router(config)# hostname Internet_Router


Internet_Router(config)# interface G0/0.10

Internet_Router(config-subif)# description Users

Internet_Router(config-subif)# encapsulation dot1q 10

Internet_Router(config-subif)# ip address 10.10.10.1 255.255.255.0

Internet_Router(config-subif)# ip nat inside

Internet_Router(config-subif)# no shutdown

Internet_Router(config-subif)# exit


Internet_Router(config)# interface G0/0.20

Internet_Router(config-subif)# description Hosters

Internet_Router(config-subif)# encapsulation dot1q 20

Internet_Router(config-subif)# ip address 20.20.20.1 255.255.255.0

Internet_Router(config-subif)# ip nat inside

Internet_Router(config-subif)# no shutdown

Internet_Router(config-subif)# exit


Internet_Router(config)# interface S1/0

Internet_Router(config-if)# description ISP2

Internet_Router(config-if)# ip address 88.207.207.10 255.255.255.252

Internet_Router(config-if)# ip nat outside

Internet_Router(config-if)# no shutdown

Internet_Router(config-if)# exit


Internet_Router(config)# router ospf 1

Internet_Router(config-router)# network 88.207.207.8 0.0.0.3 area 2

Internet_Router(config-router)# exit


Internet_Router(config)# ip dhcp pool Users

Internet_Router(dhcp-config)# network 10.10.10.0 255.255.255.0

Internet_Router(dhcp-config)# default-router 10.10.10.1

Internet_Router(dhcp-config)# exit


Internet_Router(config)# access-list 1 permit 10.10.10.0 0.0.0.255

Internet_Router(config)# access-list 1 permit 20.20.20.0 0.0.0.255


Internet_Router(config)# ip nat inside source list 1 interface G1/0 overload

Internet_Router(config)# ip nat inside source static tcp 20.20.20.2 80 88.207.207.10 80

Internet_Router(config)# ip nat inside source static tcp 20.20.20.2 443 88.207.207.10 443


Internet_Router(config)# exit


Internet_Router# copy running-config startup-config

Internet_Router# exit

### Webhost
Switch> enable

Switch# conf t


Switch(config)# hostname Webhost


Webhost(config)# vlan 10

Webhost(config-vlan)# name Users

Webhost(config-vlan)# exit


Webhost(config)# vlan 20

Webhost(config-vlan)# name Hosters

Webhost(config-vlan)# exit


Webhost(config)# interface range F0/1-2

Webhost(config-if-range)# description Users

Webhost(config-if-range)# switchport mode access

Webhost(config-if-range)# switchport access 10

Webhost(config-if-range)# exit


Webhost(config)# interface F0/24

Webhost(config-if-range)# description Hosters

Webhost(config-if)# switchport mode access

Webhost(config-if)# switchport access 20

Webhost(config-if)# exit


Webhost(config)# interface G0/1

Webhost(config-if)# switchport mode trunk

Webhost(config-if)# exit


Webhost(config)# exit


Webhost# copy running-config startup-config

Webhost# exit

### School_WIFI Access Point
SSID: EDUROAM
2.4 GHz Channel: 6
Coverage range (meters): 140.00
Authentication: WPA2-PSK, PSK Pass Phrase: ciscoedu
Encryption Type: AES

## Test scenarios
The following tests were conducted to confirm network connectivity and functionality:

  * Hosts on the school network can communicate within and between VLANs, in accordance with the configured ACL rules.
  * Hosts on the school network can access the internet and the Hoster Server using NAT, OSPF, and RIPv2.
  * All hosts, except servers, receive their IP addresses through DHCP.
  * Only hosts in the Admin VLAN can access the Admin Server.
  * Only hosts in the Teachers and Students VLANs can access the School Server.
  * Only hosts in the Admin VLAN can access the Management VLAN.

## Conclusion
  This project recreates a school network to show how key components—such as VLANs, routing, DHCP, NAT, and access controls—work together. It also offered hands-on experience designing and configuring a network in Cisco
Packet Tracer.

## Future Imrovements
The following features could help improve the network’s security and make it easier to manage:
  * Use strong passwords and secure authentication on network devices.

  * Set up secure remote access, such as SSH, to manage network devices conveniently.

## License
This project is licensed under the CC0-1.0 Universal - see the LICENSE file for details.
