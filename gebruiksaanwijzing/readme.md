# Gebruiksaanwijzing

### opladen / vervangen batterijen
De batterijen kunnen van de wagen worden gehaald door de rekker rond de arduino los te maken. Indien de batterijen te stevig vast zitten kan men steeds een schroevendraaier gebruiken om ze los te krijgen.
### draadloze communicatie
#### verbinding maken
Om verbinding te maken met de smartphone zorg je eerst dat de wagen voorzien is van de correcte spanning (de twee batterijen hebben samen >8V). Als tweede neem je de smarthpone en download je de app "Serial Bluetooth Terminal" (android). Deze app zal het mogelijk te communiceren met onze wagen. Dit gebeurt aan de hand van verschillende commando's. De meest gebruikte commando's kunnen eenvoudig in 4 drukknoppen worden verwerkt. Deze 4 knoppen zijn op de foto in het geel aangeduid. Om deze net zoals mij te programmeren druk je lang op de knop en stel je de volgende zaken in: Knop 1 -> Name: "on", Value: "run on" Knop 2 -> Name: "off", Value: "run off" Knop 3 -> Name: "debug", Value: "debug" Knop 4 -> Name: "?", "cmd"
<img width="921" height="2048" alt="image" src="https://github.com/user-attachments/assets/c327efc8-9227-470f-bbe5-b73733611ad2" />
Om de connectie te maken ga je eerst naar de bluetoothinstelling van de telefoon en zoek je "HC-05". Vervolgens maak je verbinding en gebruik je de code "1234". Eenmaal verbonden, kan je naar de app gaan en zou je deze bij "devices" moeten zien staan. Als laatste druk je op "connect" (de gele cirkel op bovenstaande foto). Als je de boodschap "connected" te zien krijgt, ben je volledig verbonden en klaar om commando's uit te sturen.


#### commando's
Er zijn verschillende commando's die gebruikt kunnen worden om parameters van de robot in te stellen, maar ook om zaken uit te lezen. De eerste 4 commando's zijn reeds verwerkt in de 4 drukknoppen en doen het volgende: "on" -> stuurt commando "run on" -> Dit zal de motoren starten en de wagen doen rijden. "off" -> stuurt commando "run off" -> Dit zal de motoren en de wagen doen stoppen. "debug" -> stuurt commando "debug" -> Je krijgt een oplijsting van alle ingestelde parameters waarmee de wagen momenteel rijdt. "?" -> stuurt commando "cmd" -> Je krijgt een oplijsting van alle mogelijke commando's die buiten de knoppen ook kunnen worden ingegeven (zie foto).
<img width="921" height="2048" alt="image" src="https://github.com/user-attachments/assets/02715f90-5cfc-4635-b8e8-6fc6501a5c3a" />
Volgende commando's kunnen dus ook nog worden ingegeven, en stellen een bepaalde parameter in: set cycle [µs]
set power [0..255]
set diff [0..1]
set kp [0..]
set ki [0..]
set kd [0..]

Als laatste zijn er nog 2 andere commando's om de sensoren te calibreren. Dit wordt hieronder verder verduidelijkt. calibrate black
calibrate white
### kalibratie
Wanneer er voor de eerste keer wordt gereden op een bepaald parkour is het belangrijk om de sensoren te calibreren. Dit zal er voor zorgen dat er een duidelijk verschil tussen wit en zwart wordt herkent.

stap 1:
Plaats de wagen op een volledig wit stuk, en voer het commando "calibrate white" in. Wacht even tot je "done" ziet verschijnen.

stap 2:
Plaats de wagen op een volledig zwart stuk, en voer het commando "calibrate black" in. Wacht even tot je "done" ziet verschijnen.

-> Nu zouden de sensoren een duidelijk verschil moeten uitlezen. Dit kan je controleren door "debug" in te voeren, en de "black" en "white" waardes te controleren. Deze moeten ver genoeg uit elkaar liggen om correct te kunnen werken.

### settings
De robot rijdt stabiel met volgende parameters:
<img width="921" height="2048" alt="image" src="https://github.com/user-attachments/assets/49f5f26d-5abc-481f-b63c-1b68b09b540b" />

