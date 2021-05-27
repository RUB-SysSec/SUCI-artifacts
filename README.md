Artifacts for the WiSec'21 paper [5G SUCI-Catchers: Still catching them all?](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2021/06/02/5G-SUCI-Catcher-WiSec21.pdf)

The PCAP contain 5G-NAS network traffic from the attacker’s perspective. All experiments are performed with two UE: OnePlus 8 and Quectel RM500Q.
## Wireshark Setup

Create a custom profile to enforce usage of the NAS dissector for packets arriving on custom ports.

```
mkdir -p ~/.config/wireshark/profiles/5G-NAS
cp wireshark-profile/* ~/.config/wireshark/profiles/5G-NAS/
```

Now open Wireshark and switch to the '5G-NAS' profile.

## PCAPs

* `standard-registration/`
  * a normal registration in a functional network
+ `suci-catcher-attack/`
  * `OnePlus_32_PersonOfInterest_found.pcapng`
    * There are 31 unsuccessful SUCI-Probes (returning Authentication Failure (MAC failure))
    * The 32nd SUCI-Probe is successful: Paket 278 is a Authentication Response. The prior Registration Request used an old SUCI.
  * `OnePlus_500_PersonOfInterest_found.pcapng`
    * Same but with more probes, demonstrating the speed
  * `Quectel_500_PersonOfInterest_found.pcapng`
    * Here the successful SUCI-Probe appears in packet 7316
* `hold-ue-in-cell/`
  * we can hold the UE effectively in a cell by repeating the attack with a pause of 8 seconds inbetween (`hold-30min*.pcapng`)
  * the pause can be at most 14 seconds (`increase-timeout-*.pcapng`)
* `auth-throtteling`: fast re-attaches to commercial networks to check for rate-throttling during authentication