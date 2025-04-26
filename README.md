# 🚨 Fake IP Phone Attack - Cisco Packet Tracer Simulation

This project demonstrates a simulated **Fake IP Phone Attack**, where a malicious device gains unauthorized access to the **Voice VLAN (VLAN 20)** by spoofing itself as an IP phone in a Cisco Packet Tracer environment.

---

## 🧠 Objective

- Understand vulnerabilities in Voice VLAN setups.
- Simulate a Fake IP Phone Attack using static IP assignment and switchport reconfiguration.
- Analyze the security risks associated with weak VLAN configurations.
- Explore preventive security measures to protect network segments.

---

## 🧰 Devices Used

| Device     | Model        | Quantity |
|------------|--------------|----------|
| Router     | Cisco 2901   | 1        |
| Switch     | Cisco 2960   | 1        |
| PC         | Generic      | 1        |
| IP Phone   | Cisco 7960   | 1        |
| Cables     | Straight-through | As needed |

---

## 🪢 Network Topology

- Router Gig0/0 connected to Switch Gig0/1 (Trunk link)
- IP Phone connected to Switch Fa0/1
- PC1 connected to Switch Fa0/2

---

## 🔧 Configuration Steps

### Switch Configuration
- VLAN 10 (DATA) and VLAN 20 (VOICE) created.
- Fa0/1: Access VLAN 10, Voice VLAN 20.
- Fa0/2: Initially access VLAN 10, modified to simulate fake IP phone.
- Gig0/1: Configured as trunk port.

### Router Configuration (Router-on-a-Stick)
- Subinterfaces configured for VLAN 10 and VLAN 20 with IP addresses.
- DHCP Pools configured for DATA and VOICE VLANs.

### Attack Simulation
- Fa0/2 port modified to include Voice VLAN.
- PC1 manually configured with static IP address from the Voice VLAN (192.168.20.x range).
- PC1 gains access to Voice VLAN traffic.

---

## ✅ Verification Steps

| Step | Command | Purpose |
|-----|---------|---------|
| 1 | `show vlan brief` | Verify VLAN assignments |
| 2 | `show interfaces trunk` | Verify trunk port configuration |
| 3 | `show ip dhcp binding` | Verify DHCP leases |
| 4 | `show ip interface brief` | Verify subinterface status |
| 5 | `show ip route` | Verify routing between VLANs |

Ping tests were successful, confirming spoofed PC1 access to the Voice VLAN.

---

## 🛡 Defense Techniques

- Enable **DHCP Snooping**
- Enable **Dynamic ARP Inspection (DAI)**
- Configure **Port Security** on access ports
- Disable unused ports and voice VLANs on unauthorized ports

---

## 📄 Files Included

- `Fake_IP_Phone_Attack.pkt` – Cisco Packet Tracer simulation file
- `Project_Report.pdf` – Full project documentation
