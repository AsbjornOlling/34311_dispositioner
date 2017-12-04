# Mobilnet: Netværkselementer og procedurer

## Punkter
* Netværksarkitekturer, inkl. formål/funktion af forskellige netværkselementer
* Procedurer: Attachment, Location Updating, Handover
* Opsætning af kald fra PSTN aboonent til GSM abbonent

## Netværksarkitekturer

### GSM arkitektur

#### Enheder:

* **MS:** Mobile Station
	- Din mobiltelefon.
* **BTS:** Base Tranciever Station
	- Indeholder radiosender og modtager
	- Ansvarlig for kryptering og dekryptering
* **BSC:** Base Station Controller
	- Kontrollerer BTS'er
	- Holder bl.a. styr på reserverede timeslots, håndtering af handovers, osv.
* **TRAU:** Transcoder and Rate Adaptation Unit
	- Forbundet til BSC
	- Transkoder signal, f.eks. mellem 13kb/s og 64 kb/s
* **MSC:** Mobile Switching Center
* **GMSC:** Gateway Mobile Switching Center
* **VLR:** Visitor Location Register
* **HLR:** Home Location Register
* **EIR:** Equipment Identification Register
* **AuC:** Authentication Center
