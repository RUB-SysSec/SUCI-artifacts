Artifacts for the WiSec'21 paper:
> SUCI-Catchers: Still catching them all?

We supply PCAP packet captures for 5G-related network communication from the attacker’s perspective. All experiments are performed with two UE: OnePlus 8 and Quectel RM500Q.

# Wireshark Setup

* create a folder ~/.config/wireshark/profiles/LTE
* copy the contents of the Wireshark profile folder to ~/.config/wireshark/profiles/LTE
* open Wireshark, change the profile to LTE (bottom right corner)

This will force dissection of packets from a couple of custom ports.

# SUCI-Catcher Attack

* for each UE, two experiments
* Person of Interest found after 32 tries
* Person of Interest found after 500 tries

OnePlus_32_PersonOfInterest_found.pcapng
    There are 31 unsuccessful SUCI-Probes (returning Authentication Failure (MAC failure))
    The 32nd SUCI-Probe is successful: Paket 278 is a Authentication Response. The prior Registration Request used an old SUCI.
OnePlus_500_PersonOfInterest_found.pcapng
    Same but with more probes, demonstrating the speed

Quectel_500_PersonOfInterest_found.pcapng
    Here the successful SUCI-Probe appears in packet 7316

# Hold UE in Cell

* we confirm that we can hold the UE in the cell, by repeating the attack with a pause of 8 seconds
* further, increase that pause and observe that the pause can be at most 14 seconds

# Standard-Attach

* this is just a standard attach to the real network without attacker present

