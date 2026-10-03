# Troubleshooting Log

This document records problems encountered while building and testing the Enterprise Network Lab. Each issue includes the problem, possible cause, solution and verification.

## Issue 1: R2 Console Password

**Problem:**
R2 displayed `User Access Verification` and requested a password before allowing access to the CLI.

**Cause:**
The router had an existing console password configured.

**Solution:**
The router configuration needs to be reset or the existing password needs to be recovered before continuing the lab configuration.

**Verification:**
After gaining CLI access, verify that the router displays the normal `R2>` or `R2#` prompt.

---

## Issue 2: OSPF Neighbor Not Forming

**Problem:**
R1 and R2 did not establish an OSPF adjacency.

**Possible Cause:**
Incorrect IP addressing, an interface being shutdown or an incorrect OSPF configuration.

**Solution:**
Check the interface status, IP addresses and OSPF configuration on both routers.

**Verification:**

```text
show ip ospf neighbor
show ip interface brief
show ip route
```

---

## Issue 3: VLAN Connectivity Failure

**Problem:**
Devices in different VLANs could not communicate.

**Possible Cause:**
Incorrect VLAN assignment, trunk configuration or router subinterface configuration.

**Solution:**
Check VLAN membership, trunk configuration and the router-on-a-stick subinterfaces.

**Verification:**

```text
show vlan brief
show interfaces trunk
```

Test connectivity using:

```text
ping <destination-ip>
```

---

## Issue 4: EtherChannel Not Forming

**Problem:**
The two links between SW1 and SW2 did not form an EtherChannel.

**Possible Cause:**
Mismatched LACP settings or different trunk configurations on the physical interfaces.

**Solution:**
Verify that both switches use LACP and that the trunk settings match.

**Verification:**

```text
show etherchannel summary
```

The physical interfaces should appear as bundled members of the port channel.

---

## Issue 5: DHCP Failure

**Problem:**
A client did not receive an IP address automatically.

**Possible Cause:**
Incorrect VLAN assignment, DHCP pool configuration, trunk configuration or excluded address range.

**Solution:**
Check the DHCP pools, VLAN assignment and trunk configuration.

**Verification:**

```text
show ip dhcp binding
```

On the client:

```text
ipconfig
```

---

## Issue 6: Guest ACL Not Working

**Problem:**
The Guest VLAN could reach the Servers VLAN when it should have been blocked.

**Possible Cause:**
The ACL was applied to the wrong interface or in the wrong direction.

**Solution:**
Check the ACL configuration and verify that it is applied inbound on the Guest VLAN subinterface.

**Verification:**

```text
show access-lists
show ip interface gigabitEthernet0/0.40
```

Then test:

```text
ping 192.168.30.10
```

The Guest client should not be able to reach the server after the ACL is correctly configured.

---

## Issue 7: SSH Connection Failure

**Problem:**
SSH access to a router or switch failed.

**Possible Cause:**
Missing RSA keys, incorrect VTY configuration, missing local user or incorrect IP connectivity.

**Solution:**
Verify the hostname, domain name, local user, RSA keys and VTY configuration.

**Verification:**

```text
show ip ssh
show running-config
```

Test SSH from a PC:

```text
ssh -l admin <device-ip>
```

---

## Issue 8: Port Security Verification

**Problem:**
Port security was not operating as expected.

**Possible Cause:**
Port security was not enabled on the access interface or the maximum MAC address setting was incorrect.

**Solution:**
Verify the access port configuration and sticky MAC learning.

**Verification:**

```text
show port-security
show port-security interface fastEthernet0/1
```

---

## Lessons Learned

This section will be completed after the lab is fully built.

Topics to document include:

* Problems that took the longest to troubleshoot
* Commands that were useful during troubleshooting
* Configuration mistakes that were made
* What was learned from each problem
* What could be configured differently in a future version of the lab
