# IP procedurer

## Fragmentering

* Det er vigtigt i internettet, at forskellige typer subnet kan kobles
* Derfor opdeling af pakker, hvis den når et net som har en mindre MTU end pakken
* **MTU:** Maximum Transfer Unit

## ARP

* **ARP:** Adress Resolution Protocol
* ARP request broadcastes, leder efter en MAC adress som svarer til IP
* ARP reply sendes kun af IP'ens indehaver
* Bruges kun på lokalnet

## NAT, NAPT og CGN

* **NAT:** Network Address Translation
	- Subnettet har en antal offentlige adresser
	- Hver gang en host vil kommunikere, bliver den givet en offentlig adresse at bruge. Routeren erstatter afsender-adressen i pakkerne.
	- Hvis der ikke er flere adresser tilgængelig, bliver pakker tabt.
* **NAPT:** Network Address and Port Translation
	- Ligesom NAT, men i stedet for at reservere hele offentlige adresser, reserveres bare en port.
	- Port specificeres i TCP/UDP header
	- NAPT bruger oftest kun én offentlig adresse
* **CGN:** Carrier Grade Nat
	- Ligesom NAPT, men flere husstande kan deles om én offentlig adresse
	- Hver husstand har én NAPT router, som samles i ISP'ens NAPT router
	- Har reserveret adresserum: `100.64.0.0/10`

## DHCP

* **DHCP:** Dynamic Host Configuration Protocol
* Protokol til at tildele IP adresser på et subnet

Typisk simpel exchange:

```
DCHP DISCOVER
		DCHP OFFER
DCHP REQUEST
		DHCP ACK
```
