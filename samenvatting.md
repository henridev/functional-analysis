# Inleiding

## situering

1. Software analyse (Ontwerpen x Programmeren)
2. Functionele analyse (business IT requirements)
3. Business Analyse 



## Inhoud

1. Analyse
2. Functionele requirements => “*Any Requirement Which Specifies* ***What The System Should Do.\*”**
3. Niet-Functionele requirements => “*Any Requirement That Specifies **How** The System Performs A Certain Function.*”
4. UX
5. Agile development - SCRUM
6. Agile development - KANBAN
7. Testing awareness

## 1. functionele requirements

### theorie

> **functioneel requirement** = 1 duidig functionaliteit vastleggen die een applicatie moet kunnen uitvoeren

> **use case** = een manier om een functionele requirement voor te stellen, beschrijft interacties tussen systeem en actor

> **use case diagram** = diagram dat een overzicht van alle rollen en functionele requirements geeft

 eigenschappen van UC:

- low-precision => globaal beeld schetsen
- voorstelling door ogen opdrachtgever
- bepaald de **Scope**
- bepaald **stakeholders**
- definieert doelen van users

opstelling via brainstorming (in groep)

- elementair business process = UC
- primary actors (uitvoerder)
- user goals
- priorities

#### onderdelen van use cases

- **domein specifieke regels** = alle technische regels voor validaties, logica .... 
- op te klaren punten = optionele vermelding van onduidelijkheden tov klant

- condities

  - **pre-conditie**
    - geeft aan wat er bij start UC moet aanwezig zijn
    - geen controle in UC
    - vaak aangever dat andere UC al gedaan is
  - **post-conditie**
    - geeft aan wat er bij uitvoeren UC moet vervuld zijn
    - bevat systeem wijziging tov domeinmodel
    - formuleren vanuit systeem standpunt
    - niet elk alternatief verloop heeft post conditie

- **body / verloop** = chronologische ordenning van **actiestappen**

  - **normaal verloop / main success story** = top to bottom beschrijving van meest voorkomende situatie waarbij doel van de primary actor grealiseerd wordt
  - **alternatieve verloop** = uitbreiding op normaal verloop
    - kan soms aanleiding wijn tot nieuwe use case
    - eindigen in success of verlatenn van use case
    - gebasseerd op wat systeem ontdekt niet wat er gebeurd is
      - ~~klant vergeet PINcode in te geven~~ => tijdslimiet overschreden bij ingave PINcode  
    - beindigd met 4 opties
      - terugkeer naar normaal verloop
      - verdergaan in stap ander normaal verloop
      - externe  / nieuwe uc oproepen
      - stopzetten huidige uc

- **stakeholder** =/= **primary actor** => belang hebben bij app maar niet bedienen =/= app bedienen

- **use case** / **elementair business process**

  - kunnen heel high level (**white versie**) zijn of  meer in detail treden (**indigo versie**) => het doel is tussen de twee blijven (**blue version**). Dit kan worden bereiktk door use cases in de vorm `WW + ZN` te zetten (ag. create invoice => beheer invoice daarentegen is weer te abstract). 

    <img src="http://www.cs.otago.ac.nz/coursework/cosc461/Image26.gif" style="zoom:100%;" />

  - 3 stappen
    - hoe? (lower level)
    - wat? (user goal - mid level) 
    - waarom? (higher level)

#### actiestappen in verloop tips

explicitiet bevestigen of annuleren overbodig tenzij ze alternatief verloop hebben

---

in een stap doet OF de actor OF de het syteem iets, niet tegelijk

---

vorm `ZN + WW + VOORWERP`

---

gebruik vogelperspectief (laat `en` weg)

---

toon vooruitgang in process

---

toon bedoeling van actor niet beweging **(geen interacties met GUI)**

---

transactie actiestap uit 4 onderdelen 

- vraag data
- valideer data
- wijzig 
- retourneer resultaat

---

vermijd if statements (valdieer controleer niet of iets ...)

- ipv systeem **controleert** passwoord **~~indien~~** correct systeem toont x <=> systeem valideert passwoord. systeem toont x

---

user laat systeem A systeem B aansturen **(geen interacties met GUI)**

- vb1 : User laat het systeem achtergrondinfo ophalen bij systeem B.
- vb2:  User signaleert het systeem data op te halen van systeem B.  => Systeem haalt achtergrondinfo op bij systeem B.

---

uc roept andere uc op

- geen calls gebruiken
- gebruik taal opdrachtgever

vb:

~~systeem valideert => user bevestigd roept UC betalen winkelmand op~~

~~systeem valideert => user bevestigd en gaat naar betalen winkelmand~~

systeem valideert => user betaalt winkelmand

### voorbeelden

```
voorbeeld UC 

ACTOR: Technieker

GOALS:
- bancontact systeem laten werken (waarom)
- leet zelftest op bancontact systeem lopen (wat)

ACTOR: Klant

GOALS:
- bancontact systeem gebruiken (waarom)
- haal geld af (wat)
- schrijf geld over (wat)
- vraag saldo op (wat)
```

```
voorbeeld PRE-CONDITIE

---

UC: gebruik applicatie (high-level)
PC: None

1. bediende logt in
2. bediende plaatst order

--- 

UC: login
PC: None

...

---

UC: plaats order
PC: bediende ingelogd

...

```

```
voorbeeld PRE-CONDITIE / POST - CONDITIE

---

UC: Haal geld Af
PA: Klant

PREC: toereikend saldo
POSTC: geld is afgehaald
```

```
voorbeeld ACTIESTAP

1. klant geeft bestelnr in
2. systeem detecteert of bestelnr == winnende nummer maand
3. systeem registreert bestelnr als winnende nummer, zendt nummer naar verkoopsdirecteur
4. systeem feliciteert klant, informeert ho prijs afhalen
```

```
Voorbeeld 1 Use Case

1. klant plaatst bankkaart in banklezer
2. systeem leest bank-id, rekeningnr + validatie met centraal banksysteem
3. klant geeft pincode in, systeem valideert pincode
4. klant kies voor geldafhandeling en geeft bedrag in
5. systeem geeft rknr, af te halen bedrag door centraal banksysteem
6. systeem geeft via centraal banksysteem bevestiging met nieuw saldo
7. systeem geeft geld, bankkaart, ticket met nieuwe saldo
8. systeem sluit transactie af

Voorbeeld 1 Use Case met alternatief verloop

1. klant plaatst bankkaart in banklezer
2. systeem leest bank-id, rekeningnr + validatie met centraal banksysteem
3. klant geeft pincode in, systeem valideert pincode
	3a. ongeldige pincode
		3a1. systeem toont gepast melding
		3a2. systeem keert terug naar stap
	3b. tijdlimiet voor ingave pincode overschreden
		3b1. systeem toont gepast melding
		3b2. systeem stopt process (post conditie afwezig)
	3c. 3 incorrecte pogingen 
		3c1. systeem toont gepast melding
		3c2. systeem blokkeert kaart
		3c3. systeem stopt process (post conditie kaart geblokkeerd)
4. klant kies voor geldafhandeling en geeft bedrag in
5. systeem geeft rknr, af te halen bedrag door centraal banksysteem
6. systeem geeft via centraal banksysteem bevestiging met nieuw saldo
7. systeem geeft geld, bankkaart, ticket met nieuwe saldo
8. systeem sluit transactie af
```

```
Voorbeeld 2 Use Case

UC: Verwerk order
1. gebruiker logt in
2. systeem toont functies, gebruiker selecteert en voert uit
	- plaats order
	- annuleer order
	- zend catalogus
3. herhaal tot gebruiker exit kiest
4. systeem logt gebruiker uit
```

```
Voorbeeld 3 UC fouten

---

1: geen syteem

UC: Haal geld Af
PA: Klant

1. klant geeft kaart en pincode in.
2. klant kies voor geldafhandeling en geeft bedrag in.
2. klant neemt geld kaart en ticket.
2. klant vertrekt.

---

2: geen actor

UC: Haal geld Af
PA: Klant

1. geeft kaart en pincode in.
2. geef geldafhandeling in en geef bedrag door.
2. neem geld kaart en ticket.
2. vertrek.

---

1+2 => correct

2: geen actor

UC: Haal geld Af
Level: User Goal
PA: Klant

1. klant plaatst bankkaart in banklezer
2. systeem leest bank-id, rekeningnr + validatie met centraal banksysteem
3. klant geeft pincode in
4. systeem valideert pincode
5. klant kies voor geldafhandeling en geeft bedrag in
6. systeem geeft rknr, af te halen bedrag door centraal banksysteem
7. systeem geeft via centraal banksysteem bevestiging met nieuw saldo
8. systeem geeft geld, bankkaart, ticket met nieuwe saldo
9. systeem logt transactie

---

3: GUI details

Use case : Koop iets
Level : user goal
Primary actor : klant

1. Systeem toont log-in scherm
2. Klant geeft user-id en paswoord in, bevestigt met “OK” aan te clicken <-- fout
3. Systeem valideert user-id en paswoord en toont scherm “Persoonlijke
Gegevens”
4. Klant geeft voornaam, fam.naam, straat, pc, woonplaats , telnr in en
bevestigt met “OK” aan te clicken
5. Systeem bevestigt dat klant reeds bestaat
6. Systeem toont artikellijst
7. Klant clickt op foto’s van de te bestellen artikels en geeft er naast aantal in, bevestigt met `“GEDAAN” aan te clicken <-- fout

---

4: teveel kleine stappen

Use case : Koop iets
Level : user goal
Primary actor : klant

1. Klant geeft user-id en paswoord in voor login
3. Systeem valideert gebruiker
4. Klant geeft naam --> teveel detail fout
5. Klant geeft woonplaats 
6. Klant geeft telnr
5. Klant selecteert producten
6. Klant geeft hoeveelheden in
7. Systeem valideert dat gebruiker bestaande klant is
8. Systeem connecteert databank
9. Systeem vraagt huidige stock op

---

3 + 4 ==> correct

Use case : Koop iets
Level : user goal
Primary actor : klant

1. Klant login via user-id en paswoord
3. Systeem valideert user
4. Klant geeft persoonlijke gegevens in
5. Systeem bevestigt dat klant reeds bestaat
6. Klant selecteert producten en hoeveelheden 
7. Systeem valideert stock

```

