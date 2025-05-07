# Rename interfaces for clarity
/interface ethernet
set [find default-name=ether2] name=Guest
set [find default-name=ether3] name=Meeting_Room
set [find default-name=ether4] name=Public_Area
set [find default-name=ether5] name=Office

# WAN - DHCP client on ether1
/ip dhcp-client
add interface=ether1 use-peer-dns=yes use-peer-ntp=yes

# Assign IPs to LAN interfaces
/ip address
add address=172.0.0.1/22 interface=Guest comment="Guest Network"
add address=192.168.20.1/23 interface=Meeting_Room comment="Meeting Room"
add address=192.168.30.1/24 interface=Public_Area comment="Public Area"
add address=10.0.0.1/24 interface=Office comment="Office Network"

# Create DHCP Pools
/ip pool
add name=pool_guest ranges=172.0.0.10-172.0.3.254
add name=pool_meeting ranges=192.168.20.10-192.168.21.254
add name=pool_public ranges=192.168.30.10-192.168.30.100
add name=pool_office ranges=10.0.0.10-10.0.0.100

# Setup DHCP Servers
/ip dhcp-server
add name=dhcp_guest interface=Guest address-pool=pool_guest lease-time=1h
add name=dhcp_meeting interface=Meeting_Room address-pool=pool_meeting lease-time=1h
add name=dhcp_public interface=Public_Area address-pool=pool_public lease-time=1h
add name=dhcp_office interface=Office address-pool=pool_office lease-time=1h

# Set DHCP Networks
/ip dhcp-server network
add address=172.0.0.0/22 gateway=172.0.0.1 dns-server=172.0.0.1
add address=192.168.20.0/23 gateway=192.168.20.1 dns-server=192.168.20.1
add address=192.168.30.0/24 gateway=192.168.30.1 dns-server=192.168.30.1
add address=10.0.0.0/24 gateway=10.0.0.1 dns-server=10.0.0.1

# Enable NAT for internet access
/ip firewall nat
add chain=srcnat out-interface=ether1 action=masquerade

# Basic firewall rules to allow established connections
/ip firewall filter
add chain=forward action=accept connection-state=established,related comment="Allow established connections"
add chain=forward action=drop connection-state=invalid comment="Drop invalid connections"

# Inter-subnet isolation (block traffic between networks)
# Guest
add chain=forward action=drop src-address=172.0.0.0/22 dst-address=192.168.20.0/23 comment="Guest to Meeting Room"
add chain=forward action=drop src-address=172.0.0.0/22 dst-address=192.168.30.0/24 comment="Guest to Public Area"
add chain=forward action=drop src-address=172.0.0.0/22 dst-address=10.0.0.0/24 comment="Guest to Office"

# Meeting Room
add chain=forward action=drop src-address=192.168.20.0/23 dst-address=172.0.0.0/22 comment="Meeting Room to Guest"
add chain=forward action=drop src-address=192.168.20.0/23 dst-address=192.168.30.0/24 comment="Meeting Room to Public Area"
add chain=forward action=drop src-address=192.168.20.0/23 dst-address=10.0.0.0/24 comment="Meeting Room to Office"

# Public Area
add chain=forward action=drop src-address=192.168.30.0/24 dst-address=172.0.0.0/22 comment="Public Area to Guest"
add chain=forward action=drop src-address=192.168.30.0/24 dst-address=192.168.20.0/23 comment="Public Area to Meeting Room"
add chain=forward action=drop src-address=192.168.30.0/24 dst-address=10.0.0.0/24 comment="Public Area to Office"

# Office
add chain=forward action=drop src-address=10.0.0.0/24 dst-address=172.0.0.0/22 comment="Office to Guest"
add chain=forward action=drop src-address=10.0.0.0/24 dst-address=192.168.20.0/23 comment="Office to Meeting Room"
add chain=forward action=drop src-address=10.0.0.0/24 dst-address=192.168.30.0/24 comment="Office to Public Area"