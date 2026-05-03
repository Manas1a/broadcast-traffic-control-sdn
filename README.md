# Broadcast Traffic Control using SDN (Mininet + Ryu)

## Problem Statement
In traditional networks, broadcast traffic (especially ARP) is flooded to all nodes, leading to unnecessary bandwidth usage and potential broadcast storms.

## Objective
To design an SDN-based solution that:
- Detects broadcast traffic
- Limits excessive flooding
- Improves network efficiency

---

## Tools Used
- Mininet
- Ryu Controller (OpenFlow 1.3)
- Open vSwitch
- Wireshark (optional)

---

## Topology
- 1 Switch (s1)
- 4 Hosts (h1, h2, h3, h4)

---

## Implementation

### Controller Logic
- Handles `packet_in` events
- Detects ARP broadcast packets
- Maintains a broadcast counter
- Drops packets after threshold
- Installs flow rules (match–action)

---

## How to Run

### Step 1: Start Controller
