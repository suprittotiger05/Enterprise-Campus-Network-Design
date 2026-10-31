# Enterprise-Campus-Network-Design
Designed and simulated an Enterprise Campus Network using Cisco Packet Tracer, implementing VLANs, subnetting, inter-VLAN routing, DHCP, 802.1Q trunking, ACLs, and STP for secure and reliable network communication.
**Level:** Beginner to intermediate  
**Target roles:** Junior Network Engineer, NOC Engineer (L1), Network Support Engineer  
**Simulation tool:** Cisco Packet Tracer

## 1. Business scenario

Design a secure, manageable campus network for a small organization with separate departments. Each department should be placed in its own VLAN so that broadcast domains are separated and access between departments can be controlled.

This is a simulated learning project. The topology and configurations are a starting design; validate them in Packet Tracer before describing the project as completed.

## 2. Project objectives

- Plan an IPv4 addressing scheme using private address space.
- Create department VLANs and assign switch access ports.
- Configure 802.1Q trunking between switches and the router.
- Configure inter-VLAN routing using router-on-a-stick.
- Configure DHCP pools for client VLANs.
- Apply an example ACL to restrict guest access to internal networks.
- Enable and verify Spanning Tree Protocol.
- Test connectivity and document results.

## 3. Proposed topology

```text
                         ISP / Internet
                               |
                         [R1 - Edge Router]
                               |
                         802.1Q trunk
                               |
                         [S1 - Core Switch]
                         /       |       \
                   trunk      access     trunk
                    /            |          \
              [S2 - Admin]  [Server]    [S3 - Users]
                 |                         |
           Admin PCs                  Staff PCs
                                     Guest Wi-Fi*
```

`*` Guest Wi-Fi is represented as a guest VLAN in this initial wired simulation. Add a wireless access point in a later extension.

### Suggested device inventory

| Device | Quantity | Purpose |
|---|---:|---|
| Router | 1 | Inter-VLAN routing and default gateway |
| Switches | 3 | VLAN segmentation and access connectivity |
| PCs | 6–10 | Department endpoint testing |
| Server | 1 | Optional DNS/HTTP services |
| Access point | Optional | Guest wireless extension |

## 4. VLAN and IP addressing plan

Use the private network `192.168.10.0/24`, divided into /26 subnets for this lab.

| VLAN | Name | Network | Default gateway | Example use |
|---:|---|---|---|---|
| 10 | ADMIN | 192.168.10.0/26 | 192.168.10.1 | Administration |
| 20 | STAFF | 192.168.10.64/26 | 192.168.10.65 | Staff |
| 30 | GUEST | 192.168.10.128/26 | 192.168.10.129 | Guest devices |
| 40 | SERVERS | 192.168.10.192/26 | 192.168.10.193 | Internal servers |

Each /26 subnet has 62 usable host addresses. Reserve low addresses for gateways and infrastructure; assign client addresses through DHCP.

## 5. Configuration plan

1. Create VLANs 10, 20, 30 and 40 on the switches.
2. Assign endpoint-facing ports to the correct access VLAN.
3. Configure switch-to-switch and switch-to-router links as 802.1Q trunks.
4. Configure router subinterfaces with 802.1Q encapsulation and gateway addresses.
5. Configure DHCP pools for the client VLANs.
6. Configure a guest ACL and apply it in the correct direction.
7. Verify STP status and ensure there are no unintended Layer 2 loops.

Starter command examples are in [`configs/`](configs/). Interface names and syntax can vary by Packet Tracer device model.

## 6. Validation checklist

Do not mark a test as passed until you have run it in your simulator and recorded evidence.

| Test | Expected result | Status |
|---|---|---|
| PC receives DHCP address in its VLAN subnet | Correct address, mask and gateway | Not tested |
| Same-VLAN hosts communicate | Successful ping | Not tested |
| Admin host reaches permitted server | Successful ping / service test | Not tested |
| Guest host reaches restricted internal subnet | Blocked by ACL | Not tested |
| Router subinterfaces are up | Interfaces show up/up | Not tested |
| Trunk carries required VLANs | VLANs visible on trunk | Not tested |
| STP has a stable forwarding topology | No unexpected loop | Not tested |

## 7. Troubleshooting approach

Use a layered method:

1. **Physical:** Check power, cables, link lights and interface status.
2. **Data link:** Check VLAN assignment, trunk allowed VLANs and STP.
3. **Network:** Check IP address, subnet mask, gateway, routes and ACLs.
4. **Transport/application:** Check service ports, DNS and server configuration.
5. Record the symptom, commands, root cause, correction and verification.

Useful commands:

```text
show ip interface brief
show vlan brief
show interfaces trunk
show spanning-tree
show running-config
show ip route
show access-lists
ping <destination-ip>
traceroute <destination-ip>
```

## 8. Repository evidence to add

- Packet Tracer `.pkt` file (if permitted by your sharing setup).
- Final topology screenshot.
- Sanitized router and switch configurations.
- IP addressing table.
- Successful and failed test evidence.
- A short troubleshooting report.

## 9. Possible extensions

- Add a second router or Layer 3 switch for gateway redundancy.
- Add HSRP/VRRP concepts if supported by the lab platform.
- Add EtherChannel/LACP between switches.
- Add wireless access with a separate guest SSID/VLAN.
- Add a firewall and simulated ISP edge.
- Add monitoring using SNMP and Zabbix in Project 3.

## 10. Completion record

Update this section only after you have completed and tested the lab.

- [ ] Built the topology in Packet Tracer
- [ ] Configured VLANs and trunks
- [ ] Configured inter-VLAN routing
- [ ] Configured DHCP
- [ ] Applied and tested the guest ACL
- [ ] Verified STP
- [ ] Completed the validation checklist
- [ ] Added screenshots and configuration evidence

**Learning note:** This lab demonstrates foundational enterprise LAN design. It does not by itself represent production deployment experience.
