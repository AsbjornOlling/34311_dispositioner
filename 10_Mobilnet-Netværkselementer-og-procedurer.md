# Mobilnet: Netværkselementer og procedurer 

## Punkter
* Procedurer: Attachment, Location Updating, Handover
* Opsætning af kald fra PSTN aboonent til GSM abbonent

## GSM Netværksarkitektur

### Enheder:

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
	- Forbinder samtaler mellem mobile brugere og andre brugere (både mobil og fastnet)
	- Én MSC styrer et antal BSC'er
	- MSC beder f.eks. en BSC om at reservere et timeslot
* **GMSC:** Gateway Mobile Switching Center
	- En type MSC, som også forbindre til andre netværk (end mobilnetværk).
* **VLR:** Visitor Location Register
	- En database, som er tilknyttet en MSC.
	- Indeholder info om brugere, deres lokation, og hvilke tjenester de har adgang til.
	- Kun info om brugere, som er 'hører til' en given MSC.
* **HLR:** Home Location Register
	- En database, som har info om alle operatørens abbonenter.
	- HLR viser, hvilken VLR har info om brugeren p.t..
	- HLR viser også, om brugerens telefon roamer, eller er slukket.
* **EIR:** Equipment Identification Register
	- Indeholder info om spærrede mobiltelefoner.
	- Står som **IMEI** (*International Mobile Equipment Identifier*) numre.
* **AuC:** Authentication Center
	- Sikkerhedsrelateret info om abonnenter.
	- Sørger for "log-on"-agtigt procedure.

![GSM topologi](gsm_map.png)

### Andre arkitekturer:

#### GPRS/EDGE
Udbygning af GSM, til pakkekoblet data

**Nye enheder:**
- **PCU:** Packet Control Unit
	- Sidder fast på en BSC
	- Bestemmer hvilke (MTS-)timeslots og rammer en mobil sender i
* **SGSN:** Serving GPRS Support Node
	- Basically det samme som en MSC, men pakkekoblet.
	- Håndterer celleskift
	- Håndterer også error control
* **GGSN:** Gateway GPRS Support Node
	- Basically det samme som en GMCS
	- Forbinder til andre pakke-koblede netværk (dvs. internettet)

#### **UMTS/HSDPA/HSUPA**
*Ikke* en udbygning af GSM - helt ny netværksarkitektur.



## Procedurer

### Attachment
1. Mobiltelefonen scanner GSM-frekvenser efter info om netværket
2. Hvis netværket tilhører en godkendt operatør, prøver telefonen at registrere sig på netværket ved at sende IMEI og IMSI (*International Mobile Subscriber Identity*) numre - til MSC.
3. Netværket etablerer kyptografisk forbindelse vha. AuC (*challenge-response* metode til key-exchange).
4. MSC'en sneder info til HLR - VLR opdateres.
5. MSC sender signal til mobilen for at beskræfte at proceduren er gennemført.

#### Attachment i UMTS og LTE


#### Detachment
1. Når man slukker telefonen, sender den et *detach*-signal til MSC.
2. MSC sletter info i VLR

#### Location Updating
#### Handover

## Opsætning af kald fra PSTN til GSM
