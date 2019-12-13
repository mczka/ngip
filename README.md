# ngip concept
the Next Generation of Internet Protocol

What if this Western civilization falls?
And all the Intellectual Property will go in the dust.

Let's make a new protocol for communication from the beginning!

Background:
IPv4 deplection now and after 20 year of RFC ipv6 has not been transitioned yet

Requirements:
- exascale/HPC
- flat network, easy to adopt into the Cloud, virt world
- easy integrade into PCI express bus or ng PCIe
- multi vCPU aware
- ECMP
- BGP lw as dynamic routing

Descriptions of ngip
- Layer 1: use ethernet frame (ethernet is everywhere) more than 64B we can use in protocol header
- Layer 234 merge into one header <IPmtu, HL, FLAG, CRC FLAG, interfaceID, PL, dst IP, src IP,dst tag, src tag, payload>


 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |               |               |                               |
 +      MTU      +  Hop Limit    +              FLAG             +
 |               |               |                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |                               |                               |
 +           FLAG/CRC            +         Payload Length        +
 |                               |                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |                                                               |
 +                                                               +
 |                                                               |
 +                          Interface ID                         +
 |                                                               |
 +                                                               +
 |                                                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |                                                               |
 +                                                               +
 |                                                               |
 +                      Destination Address                      +
 |                                                               |
 +                                                               +
 |                                                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |                                                               |
 +                                                               +
 |                                                               |
 +                         Source Address                        +
 |                                                               |
 +                                                               +
 |                                                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |                                                               |
 +                                                               +
 |                                                               |
 +                        Destination Tag                        +
 |                                                               |
 +                                                               +
 |                                                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 |                                                               |
 +                                                               +
 |                                                               |
 +                           Source Tag                          +
 |                                                               |
 +                                                               +
 |                                                               |
 +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+



IPmtu - the MTU maximum.
HL -  Hop Limit 16-bit unsigned integer. Decremented by 1 by each node that forwards the packet. The packet is discarded if Hop Limit is decremented to zero.
FLAG - flags
CRC FLAG - error correction ?
interfaceID
PL - Payload Length 32-bit unsigned integer. Length of the ngIP payload in bytes, the rest of the packet following this ngIP header.
dst IP - 128-bit address of the recipient of the packet.
src IP - 128-bit address of the originator of the packet.
dst tag - 128-bit unsigned integer.
src tag - 128-bit unsigned integer.
payload

HL - Hop Limit
if packet forwarding then HL=HL-1
if HL=0, drop packet.
if IPng:FLAG = LL then HL=1.

flags
LL - link local
ST - stack IP
