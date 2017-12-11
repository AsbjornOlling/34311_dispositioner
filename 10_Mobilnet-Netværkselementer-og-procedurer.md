# Mobilnet: Netværkselementer og procedurer 

## Punkter
* Procedurer: Attachment, Location Updating, Handover
* Opsætning af kald fra PSTN aboonent til GSM abbonent

## Netværksarkitekturer

### GSM

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

 Andre arkitekturer:

### GPRS/EDGE
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

### UMTS/HSDPA/HSUPA

Ny netærksarkitetktur *vidreudvikling* af GSM.

* Terminalen kaldes nu **UE** (User Equipment).
* **UTRAN:** Terrestrial Radio Access Network
	- Et nyt accessnetværk, indeholder nye enheder:
		+ **Node B**
			* Opgraderet version af BTS
			* Højere kapacitet
			* Laver nu CDMA multiplexing
		* **RNC:** Radio Network Controller
			- Bare en BSC til Node B
* **HSDPA/HSUPA:** bare højere kapacitet...


### LTE
* Bedre kapacitet igen
* Udelukkende pakkekoblet (dvs. VOIP (VOLTE) til tale)
* Nye enheder:
	- **eNode B:**
		- "Node B på steroider" -*Staalhagen*
		- Nu med intereferens-styring
	* **sGW:** Serving Gateway
		- Ligesom MSC
		- Vidresender pakker til PDN-GW
	- **PDN-GW:** Packet Data Network GateWay
		- En gateway til internettet.
		- Tildeler IP-adresser til UE'er
	* **MME:** Mobility Management Entity
		- Ansvarlig for authenificering (ligesom AuG)
		- MME kontakter PDN-GW for at bede om en IP til UE'en
	- **HSS:** Ny HLR Ny HLR


## Procedurer

### Attachment og detachment (i GSM)
1. Mobiltelefonen scanner GSM-frekvenser efter info om netværket
2. Hvis netværket tilhører en godkendt operatør, prøver telefonen at registrere sig på netværket ved at sende IMEI og IMSI (*International Mobile Subscriber Identity*) numre - til MSC.
3. Netværket etablerer kyptografisk forbindelse vha. AuC (*challenge-response* metode til key-exchange).
4. MSC'en sneder info til HLR - VLR opdateres.
5. MSC sender signal til mobilen for at beskræfte at proceduren er gennemført.

#### Detachment (i GSM)
1. Når man slukker telefonen, sender den et *detach*-signal til MSC.
2. MSC sletter info i VLR

#### Attach og detach i UMTS og LTE
Næsten same shit, men UMTS og LTE checker om base-stationen er legit, for at undgå falske base-stationer. I GSM er et Man-in-the-Middle angreb muligt.

### Location Area Updating (i GSM)
1. Mobil lægger mærke til broadcasts fra en ny BTS
2. Mobil sender location update besked til MSC
3. MSC beder om info om bruger fra HLR
4. HLR returnerer info, som MSC gemmer i VLR
5. MSC kvitterer for modtaget info
6. HLR instruerer gammel MSC om at slette VLR info

#### Location *Routing* Update i GPRS / EDGE, UMTS
I GPRS / EDGE kaldes det *Routing Area* i stedet for *Location Area*.
Ellers rimelig meget det samme.

#### Tracking Area Update LTE
LTE inddeler UE'en i tracking areas, og laver altså også Tracking Area updates. Ellers er det meget det samme.

### Handover (i GSM)
Når et dataflow skiftes fra en celle til en anden.

1. Enten BTS eller MS (mobilen) måler lav signalstyrke ifht. andre tilgængelige signaler. 
2. BSC lægger mærke til, at målingen er lav.
3. Hvis nye celle er hos en anden MSC, håndteres handover af MSC
4. Hvis nye celle er hos samme MSC, håndteres handover af BSC.

#### Handover i UTMS
UMTS kan lave to slags handover: gammeldags GSM handover (aka *hard handover*) eller:

**Soft handover:** når der er simultan (redundant) forbindelse til to Node B'er under handover

OBS: *hard handover* er ikke et problem i normal samtale, men kan være problematisk til data.

#### Handover i LTE
... der er meget mere at sige om handover end der står i det her afsnit.

## Opsætning af kald fra PSTN til GSM




