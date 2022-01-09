Pas het volgende normal verloop aan waar nodig zodat het aan de regels voldoet zoals in de theorie gezien

Normaal verloop:

1. Klant plaatst bankkaart in kaartlezer
2. Systeem leest bank-id, rekeningnr en valideert deze met het centraal banksysteem
3. Klant geeft pincode in, systeem valideert pincode
4. Klant kiest voor geldafhaling en geeft bedrag in
5. Systeem geeft rekeningnr, af te halen bedrag door aan centraal banksysteem
6. Systeem geeft ,via centraal banksysteem, bevestiging samen met het nieuwe saldo
7. Systeem geeft geld, bankkaart en ticket met nieuw saldo
8. Systeem sluit transactie af

---

1. Klant plaatst bankkaart in kaartlezer
   - FOUT: doel van bankkaart invoeren is gegevens aan systeem doorgeven
   - BETER: De klant voert zijn aanmeldgegevens in
2. Systeem leest bank-id, rekeningnr en valideert deze met het centraal banksysteem
   - FOUT: lezen is te technisch
   - FOUT: valideer met welk systeem te technisch
   - BETER: Het systeem valideert of het bank-id en rekeningnummer overeenstemmen
3. Klant geeft pincode in, systeem valideert pincode
   - FOUT: stap ervoor is validatie dus deze kan niet ingave zijn (actie zonder vraag systeem)
   - FOUT: combinaties twee acties
   - BETER: Systeem vraagt pincode
   - BETER: Klant geeft pincode
   - BETER: Systeem valideert pincode
4. Klant kiest voor geldafhaling en geeft bedrag in
   - FOUT: actie zonder vraag systeem
   - FOUT: kiezen voor deze actie niet nodig want is use case op zich
   - BETER: Systeem vraagt gewenste bedrag
   - BETER: Gebruiker geeft gewenste bedrag
5. Systeem geeft rekeningnr, af te halen bedrag door aan centraal banksysteem
   - FOUT: geef door aan specifiek systeem technisch
   - FOUT: beschrijft hoe ipv wat
   - FOUT: mist validatie
   - BETER: Systeem valideert of saldo toereikend is
   - BETER: Systeem verminderd saldo van gebruiker met gegeven bedrag
6. Systeem geeft ,via centraal banksysteem, bevestiging samen met het nieuwe saldo
   - FOUT: geef door aan specifiek systeem technisch
   - BETER: Systeem geeft bevestiging met nieuw saldo
7. Systeem geeft geld, bankkaart en ticket met nieuw saldo
   - FOUT: beschrijving fysieke stap na slagen use case
   - BETER: weglaten
9. Systeem sluit transactie af
   - FOUT: geen actiestap / geen meerwaarde
   - BETER: weglaten


---

OPLOSSING:

1. De klant voert zijn aanmeldgegevens in
2. Het systeem valideert of het bank-id en rekeningnummer overeenstemmen
3. Het systeem vraagt de pincode
4. De klant voert de pincode in
5. Het systeem valideert of de pincode geldig is
6. Het systeem vraagt het gewenste bedrag
7. De klant voert het bedrag in
8. Het systeem valideert of het saldo van de klant toereikend is voor het af te halen bedrag
9. Het systeem vermindert het saldo van de klant met het af te halen bedrag
10. Het systeem toont een bevestiging en het nieuwe saldo