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
export EVENTLET_NO_GREENDNS=yes
ryu-manager broadcast_control.py


### Step 2: Start Mininet

sudo mn --custom topo.py --topo broadcasttopo --controller=remote


---

## Test Scenarios

### Scenario 1: Normal Communication

pingall

All hosts communicate successfully.

---

### Scenario 2: Broadcast Traffic Control

h1 ip neigh flush all
h1 arping -c 10 10.0.0.2


### Observed Behavior:
- Broadcast packets detected
- Excess packets dropped after threshold

---

## Performance Analysis

### Latency

h1 ping h2


### Throughput

iperf h1 h2


---

## Flow Table Verification

sudo ovs-ofctl dump-flows s1


---

## Results
- Broadcast traffic successfully detected
- Flooding reduced after threshold
- Network performance improved
- Flow rules dynamically installed

---

## Screenshots

### 1. Ping Test
![Ping](screenshots/pingall.png)

### 2. Broadcast Detection
![ARP](screenshots/arping.png)

### 3. Controller Logs
![Logs](screenshots/controller_logs.png)

### 4. Flow Table
![Flows](screenshots/flows.png)

### 5. Throughput Test
![Iperf](screenshots/iperf.png)

---

## Conclusion
The SDN-based approach effectively controls broadcast traffic by dynamically installing flow rules and limiting unnecessary flooding, improving network efficiency.

---

## References
- Mininet Documentation
- Ryu SDN Framework
- OpenFlow Specification
