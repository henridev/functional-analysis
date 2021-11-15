Oefening:

Stel een UCD op voor een bibliotheek met minstens:

3 rollen
1 extends
1 inlcude

---

Let op: dit is een modeloplossing en zeker niet de enigste juiste oplossing!

In de modeloplossing wordt er gebruikt gemaakt van volgende rollen:

Lid: persoon die gekend is bij de bibliotheek (d.m.v. een lidkaart). Deze kan o.a. een item ontlenen, ontlening verlengen, item terugbrengen, item opzoeken, item reserveren, ...
Bibliothecaris: dit is een medewerker van de bibliotheek. Deze persoon kan o.a. item opzoeken, ontleningen raadplegen, item toevoegen aan de catalogus, item verwijderen uit de catalogus, ...
Gebruiker: dit is een persoon die niet gekend is in de bibliotheek, m.a.w. een anoniem persoon. Deze persoon kan enkel een item opzoeken
We plaatsen in eerste instantie alle rollen en hun use cases in het diagram zonder gebruik te maken van includes/extends.

Dit levert voorlopig volgend use case diagram op:

<img src="https://res.cloudinary.com/dri8yyakb/image/upload/v1636960992/ucd_bib_pwd8vb.png"/>
 

Nu kijken we welke uitbreidingen er mogelijk zijn door gebruik te maken van includes of extends. Hieronder volgen slechts enkele voorbeelden, andere zijn mogelijk.

Extends - Boete betalen

In eerste instantie kunnen we bevoorbeeld kijken naar uitzonderingen die kunnen optreden wanneer een item wordt teruggebracht (of net niet). Het valt wel eens voor dat een item te laat
werd teruggebracht. In dat geval zal er een boete dienen betaalt te worden. Uiteraard is het zo dat er slechts in een klein aantal gevallen van items die teruggebracht worden ook effectief
een boete moet betaald worden. Het merendeel van de items wordt op tijd terug bezorgd. Dit zorgt er voor dat het betalen van een boete zeker geen onderdeel is van het normale verloop
van de use case "item terugbrengen" maar dus eerder een uitzondering en dus een alternatief verloop zal zijn. Er wordt hier wel verondersteld dat de boete onmiddellijk wordt vereffend bij
het terugbrengen van het item. Hierdoor zal de use case "boete betalen" als extends optreden naar de use case "item terugbrengen".

Extends - Item reserveren

Als tweede voorbeeld van een uitzondering kunnen we ook de functionaliteit "item reserveren" beschouwen als uitzondering. De functionaliteit op zich kan perfect bestaand waarbij het lid
een item wenst te reserveren voor een latere periode. Het is ook mogelijk dat een lid het item wil reserveren als het niet gevonden werd tijdens de functionaliteit "item opzoeken". De use 
case "item reserveren" bestaat dus als rechstreeks oproepbare functionaliteit maar ook als extends naar de use case "item opzoeken". Merk wel op dat omdat de use case "item opzoeken"
als primaire actor "Lid" heeft, dit er voor zorgt dat een Gebruiker geen item kan reseveren, ook al is de functionaliteit als extends met de functionaliteit "item opzoeken" verbonden.

Includes - Item opzoeken

In de vorige oplossing hebben we "item ontlenen" en "item opzoeken" als losse functionaliteiten beschouwt. Echter zijn deze in realiteit nauw met elkaar verbonden. Een lid kan immers geen
item ontlenen zonder het eerst opgezocht hebben. Het lid heeft met andere woorden eerst nood aan de details van een item (b.v.: gangnummer, itemcode, beschikbaarheid, ...) voor het in de 
bibliotheek kan teruggevonden worden en dus ook uitgeleend worden. Dit mechanisme kan je echter op twee manieren in een use case gieten. Ofwel neem je bij de use case van "item ontlenen"
een preconditie op dat er een item moet opgezocht zijn. Hierdoor wordt dan verondersteld dat het lid het item al effectief ook gevonden heeft. In onze oplossing kiezen we echter voor de tweede
manier, waarbij we tijdens het verhaal om een item te onlenen het ook eerst nog gaan opzoeken. Hierdoor zal de use case "item ontlenen" de functionaliteit van "item opzoeken" omvatten en 
dus als includes in het UCD aangeduid worden.

Als volledige modeloplossing krijgen we dan

<img src="https://res.cloudinary.com/dri8yyakb/image/upload/v1636960993/ucd_bib_incl_ext_bsmymf.png"/>