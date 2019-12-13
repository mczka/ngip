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

Descriptions of ngip
- Layer 1: use ethernet frame (ethernet is everywhere) more than 64B we can use in protocol header
- Layer 234 merge into one header <IPmtu, HL, FLAG, CRC FLAG, interfaceID, PL, dst IP, src IP,dst tag, src tag, payload>
IPmtu
HL
FLAG
CRC FLAG
interfaceID
PL
dst IP
src IP
dst tag
src tag
payload
