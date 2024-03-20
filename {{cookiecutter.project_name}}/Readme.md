## Ansible Specific
- To check vagrant vms are accessible from anisble
```
ansible all  -m ping
```
- To check vagrant vms are accessible from anisble
```
ansible all -m ping -i environments/preprod/inventory.txt
```

## Vagrant Specific
### VirtualBox Networking with vboxnet0
- To check vagrantbox network details/range
```
VBoxManage list hostonlyifs
```
Output
```
Name:            vboxnet0
GUID:            786f6276-656e-4074-8000-0a0027000000
DHCP:            Disabled
IPAddress:       192.168.56.1
NetworkMask:     255.255.255.0
IPV6Address:     
IPV6NetworkMaskPrefixLength: 0
HardwareAddress: 0a:00:27:00:00:00
MediumType:      Ethernet
Wireless:        No
Status:          Down
VBoxNetworkName: HostInterfaceNetworking-vboxnet0
```
#### VirtualBox Networking with vboxnet0
- `vboxnet0` is a host-only network adapter created by VirtualBox.
- It enables network communication between the host machine and virtual machines (VMs) without external network access.

Network Configuration:
- Subnet: 192.168.56.0/24
- Subnet Mask: 255.255.255.0
- Host's VirtualBox Adapter IP: 192.168.56.1 (acts as the default gateway for this subnet)
- DHCP: Disabled (static IP configuration is typically used for VMs on this adapter)

Usable IP Addresses for VMs:
- Range: 192.168.56.2 to 192.168.56.254
- These IPs can be assigned to VMs for inter-VM communication on the same host.

The gateway address (192.168.56.1) is reserved for the `vboxnet0` network adapter and should not be assigned to VMs. VirtualBox manages the routing of traffic from the VMs to the host through this gateway IP.


## MySQL Specific
- Check if MySQL replication is working or not; 
Option-1:
Do below command in `vm2/slave` in mysql
```
SHOW SLAVE STATUS\G;
```
Option-2:
Do below command in `vm1/master` in mysql
```
CREATE DATABASE IF NOT EXISTS testdb;
USE testdb;
CREATE TABLE repl_test (id INT NOT NULL AUTO_INCREMENT, val VARCHAR(50), PRIMARY KEY(id));
INSERT INTO repl_test (val) VALUES ('Replication check');
```
Do below command in `vm2/slave` in mysql
```
USE testdb;
SELECT * FROM repl_test;
```