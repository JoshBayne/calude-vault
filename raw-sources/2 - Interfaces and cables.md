## RJ-45  
RJ stands for Registered Jack

## Ethernet
Collection of network protocols and standards

## Network protocols
IP internet protocol

## Bits and Bytes
bits made up of 0s or 1s
8 bits make 1 byte
speed measured in bits per second
data on hard drive measured in bytes

1Kb = 1000 bits
1Mb = 1000000 bits
1Gb = 1000000000 bits
1Tb = 1000000000000 bits

Ethernet Standards
Defined in IEEE 802.3 standard in 1983
IEEE - Institute of Electrical and Electronics Engineers

## Ethernet Standards (copper)
| Speed    | Common Name      | IEEE Standard | Informal Name | Max Length |
| -------- | ---------------- | ------------- | ------------- | ---------- |
| 10 Mbps  | Ethernet         | 802.3i        | 10BASE-T      | 100M       |
| 100 Mbps | Fast Ethernet    | 802.3u        | 100BASE-T     | 100M       |
| 1 Gbps   | Gigabit Ethernet | 802.3ab       | 1000BASE-T    | 100M       |
| 10 Gbps  | 10 Gig Ethernet  | 802.3an       | 10GBASE-T     | 100M       |

## UTP Cables
**U**nshielded **T**wisted **P**air
Vulnerable to electrical interference
4 pairs of wires, 8 wires in total

10BASE-T and 100BASE-T only use 2 pairs (4 wires)
1000BASE-T and 10GBASE-T use all 4 pairs (8 wires)

### 10BASE-T and 100BASE-T
#### Client to Switch
Pins 1 and 2 on client Transmit (Tx) and connect to 1 and 2 on the switch which Receives (Rx) 
Pins 3 and 6  on client Receive(Rx) and connect to 3 and 6 on switch which Transmits (Tx)
This is called Full-Duplex, both devices can transmit and receive at the same time

#### Switch to Router
Pins 1 and 2 Transmit (Tx) on router and connect to 1 and 2 on the switch which Receives (Rx) 
Pins 3 and 6 Receive (Rx) on router and connect to 3 and 6 on switch which Transmits (Tx)
This is called Full-Duplex, both devices can transmit and receive at the same time

Straight-through cable - cable connects directly from one device to another to the **same pins**

#### Router to Router, Switch to Switch, Client to Client, and Client to Router
Communication cannot occur since they want to transmit and receive onto the same pins
Need a **crossover cable** - Pin 1 connects to pin 3, 2 to 6



| Device type | Transmit (Tx) Pins | Receive (Rx) Pins |
| ----------- | ------------------ | ----------------- |
| Router      | 1 and 2            | 3 and 6           |
| Firewall    | 1 and 2            | 3 and 6           |
| PC          | 1 and 2            | 3 and 6           |
| Switch      | 3 and 6            | 1 and 2           |


Auto MDI-X - allows device to detect which pins a connected device is transmitting from, and switches the pins that Tx and Rx

### 1000BASE-T and 10GBASE-T
pins 4 and 5 pair
pins 7 and 8 pair
Each pair is bidirectional, can transmit and receive



## Fibre-Optic Connections
SFP - Small Form-Factor Pluggable
Fiber cable send light signals over glass fibers
Each cable made of a pair of strands, one to transmit and one to receive

Made up on 
- Fibreglass core
- Cladding that reflects light
- protective buffer
- outer cable jacket

Multimode Fiber
Wider core diameter than single mode Fiber
Allows multiple angles (modes) of light waves to enter the fiberglass core
allowers longer cables than UTP. but still shorter than single mode fiber
Cheaper than single-mode fiber (use cheaper LED SFP transmitters)

Single-Mode Fiber
Core diameter is narrower than Multimoder
Light enters at a single angle (mode) from a laser-based transmitter
allows longer cable lengths than UTP and Multimode Fiber
more expensive than multimode (due to expensive laser-based SFP transmitters)

### Fiber Optic Cable Standards

| Informal Name | IEEE Standard | Speed   | Cable Type           | Max Length          |
| ------------- | ------------- | ------- | -------------------- | ------------------- |
| 1000BASE-LX   | 802.3z        | 1 Gbps  | Multi or single mode | 550m (MM) 5 km (SM) |
| 10GBASE-SR    | 802.3ae       | 10 Gbps | Miltimode            | 400m                |
| 10GBase-LR    | 802.3ae       | 10 Gbps | Single-Mode          | 10 km               |
| 10GBASE-ER    | 802.3ae       | 10 Gbps | Single-Mode          | 30 km                    |


## UTP vs Fiber Optic
UTP
- loser cost
- shorter max distance (~100m)
- Can be vulnerable to EMI (electromagnetic interference)
- RJ45 ports with UTP are cheaper
- Emits (leaks) a faint signal outside cable, which can be copied

Fiber
- More expensive
- Longer max distance
- Not vulnerable to EMI
- SFP ports are more expensive (single mode more expensive than multimode)
- Does not leak any signal outside the cable

