# Test Results

## Network Connectivity
- Verified router interface IP addresses.
- Enabled IPv4 forwarding on the router.
- Confirmed ICMP connectivity between Client-A (`192.168.10.10`) and Client-B (`192.168.20.10`).

## Firewall and SSH Security
- Configured UFW to control routed traffic.
- Tested SSH connectivity between Client-A and Client-B.
- Enabled SSH public-key authentication.
- Disabled password-based SSH authentication and root login.
- Verified that password-only SSH login was rejected.

## Packet Analysis
- Captured network traffic using `tcpdump`.
- Opened the packet capture in Wireshark.
- Inspected ICMP echo requests and replies.
- Saved packet captures in `packet-captures/`.

## Suricata IDS
- Installed and configured Suricata on the Ubuntu router.
- Added custom detection rules in `rules/local.rules`.
- Generated custom ICMP and SSH alerts.
- Verified alerts in `/var/log/suricata/fast.log`.
- Confirmed that the Suricata service was running.

## Evidence
- Screenshots: `screenshots/`
- Packet captures: `packet-captures/`
- Custom rules: `rules/local.rules`

## Conclusion
This lab demonstrates Linux-based network monitoring, subnet routing, firewall configuration, SSH hardening, packet analysis, and custom intrusion detection in a VirtualBox environment.
