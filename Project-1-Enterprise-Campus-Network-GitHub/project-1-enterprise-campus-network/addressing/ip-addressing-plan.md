# IP Addressing Plan

Parent network: `192.168.10.0/24`

| VLAN | Name | Subnet | Mask | Gateway | Usable range |
|---:|---|---|---|---|---|
| 10 | ADMIN | 192.168.10.0/26 | 255.255.255.192 | 192.168.10.1 | 192.168.10.1–62 |
| 20 | STAFF | 192.168.10.64/26 | 255.255.255.192 | 192.168.10.65 | 192.168.10.65–126 |
| 30 | GUEST | 192.168.10.128/26 | 255.255.255.192 | 192.168.10.129 | 192.168.10.129–190 |
| 40 | SERVERS | 192.168.10.192/26 | 255.255.255.192 | 192.168.10.193 | 192.168.10.193–254 |

For a real deployment, reserve infrastructure addresses consistently and document DHCP exclusions. This is a lab addressing plan; adjust it if your chosen topology or device model requires different addressing.
