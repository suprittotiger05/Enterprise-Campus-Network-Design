# Connectivity Test Log

Run each test in Packet Tracer and replace `Not tested` with the actual result. Add screenshots or command output under this folder.

| Test ID | Test | Expected result | Actual result | Status |
|---|---|---|---|---|
| T-01 | ADMIN PC obtains DHCP lease | 192.168.10.0/26 subnet | — | Not tested |
| T-02 | STAFF PC obtains DHCP lease | 192.168.10.64/26 subnet | — | Not tested |
| T-03 | Same-VLAN host-to-host ping | Success | — | Not tested |
| T-04 | Inter-VLAN ping from permitted ADMIN host | Success | — | Not tested |
| T-05 | GUEST host to ADMIN subnet | Blocked | — | Not tested |
| T-06 | GUEST host to STAFF subnet | Blocked | — | Not tested |
| T-07 | Router subinterfaces | Up/up | — | Not tested |
| T-08 | Switch trunk VLAN list | VLANs 10,20,30,40 allowed | — | Not tested |
| T-09 | STP status | Stable, no unintended loop | — | Not tested |

## Evidence record

For every test, record:
- Date and simulator/device model
- Source and destination
- Command or action
- Expected result
- Actual result
- Screenshot filename
- Pass/fail and explanation
