# Test Results

This document records the observed results of tests performed in the Linux Network Monitoring & Security Lab.

## 1. Network Connectivity Test

**Test:** Ping Client-B from Client-A.

**Command:**
```bash
ping -c 4 192.168.20.10
```

**Expected:** Client-B responds to ICMP Echo Requests.

**Observed:** 4 packets transmitted, 4 received, 0% packet loss.

**Result:** PASS

## 2. Unreachable Host Test

**Test:** Ping an unused address in the Client-B subnet.

**Command:**
```bash
ping -c 4 192.168.20.11
```

**Expected:** No successful reply if the address is unused.

**Observed:** The router returned `Destination Host Unreachable` for all four requests.

**Result:** PASS — the expected unreachable response was observed.

## 3. SSH Authentication Test

**Test:** Connect to Client-B from Client-A using SSH public-key authentication.

**Target:** `192.168.20.10`

**Expected:** Authentication succeeds with the configured SSH key.

**Observed:** Key-based SSH login was successful during testing.

**Result:** PASS

## 4. SSH Password Authentication Test

**Test:** Attempt password-only authentication while public-key authentication is disabled for the client command.

**Expected:** Password-only authentication is rejected by the SSH server.

**Observed:** The server returned `Permission denied (publickey)`.

**Result:** PASS

## 5. Wireshark Packet Analysis

**Test:** Inspect the saved packet capture in Wireshark.

**Display filter:**
```text
icmp
```

**Expected:** ICMP Echo Requests and Echo Replies are visible.

**Observed:** Packets between `192.168.10.10` and `192.168.20.10` were visible in the capture.

**Result:** PASS

## 6. Suricata Service Test

**Test:** Check whether the Suricata service is running.

**Command:**
```bash
sudo systemctl status suricata --no-pager
```

**Expected:** The service state shows `active (running)`.

**Observed:** The service was confirmed active after the configuration was corrected.

**Result:** PASS

## 7. Custom ICMP Detection Test

**Test:** Generate ICMP traffic from Client-A to Client-B while monitoring Suricata alerts.

**Alert log:**
```text
/var/log/suricata/fast.log
```

**Expected:** A matching custom ICMP alert is generated.

**Observed:** The log displayed `LAB ICMP traffic from Client-A to Client-B network`.

**Result:** PASS

## 8. Custom SSH Detection Test

**Test:** Initiate an SSH connection from Client-A to Client-B while monitoring Suricata alerts.

**Expected:** A matching custom SSH alert is generated.

**Observed:** The log displayed `LAB SSH connection from Client-A to Client-B`.

**Result:** PASS

## Summary

The recorded tests demonstrate successful inter-subnet connectivity, SSH key-based authentication, rejection of password-only SSH authentication, packet inspection in Wireshark, and custom ICMP and SSH alert generation by Suricata.

Supporting evidence is available in the [`screenshots/`](../screenshots/) and [`packet-captures/`](../packet-captures/) directories.
