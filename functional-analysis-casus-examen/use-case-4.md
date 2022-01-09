# use case 4

=> vraag of 2 functionaliteiten niet in dezelfde use-case moeten komen

Use case: Motivatie afkeuren

Primary actor: Lector

Precondities: Cursist draagt een gb nominatie voor, Lector is aangemeld
Postcondities: Cursist kan motivatie herwerken

Normaal verloop:

1. De Lector vraagt een gb-groep motivatie op
2. Het systeem retourneert de motivatie, omschrijving en takenlijst voor de gb-groep nominatie
3. Het systeem vraagt de goedkeuring of afkeuring van de nominatie met feedback
4. De Lector geeft feedback
5. De Lector confirmeert afkeuring van gb-groep nominatie
6. Het Systeem valideert de afkeuring en feedback
7. Het Systeem registreert de afkeuring en feedback
8. Het Systeem retourneert de confirmatie van de registratie

Alternatieve verlopen:

5a. ongeldige feedback input
    5a1. Systeem toont foutmelding
    5a1. Systeem retourneert naar stap 3

Domeinspecifieke regels:

DR_feedbackvalidatie:

de feedback mag niet leeg zijn

Op te klaren punten:
