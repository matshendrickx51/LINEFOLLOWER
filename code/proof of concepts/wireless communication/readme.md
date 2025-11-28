# draadloze communicatie proof of concept
Minimale hard- en software waarmee aangetoond wordt dat duplex kan gecommuniceerd worden tussen de microcontroller en een smartphone, gebruik makend van de HC-05 Bluetoothmodule.
Om de werking van de bluetoothmodule te demonstreren is een code geschreven waarbij we in 2 richtingen communiceren.

## Functionaliteit:
Als eerste zal de microcontroller een drukknop uitlezen en doorsturen naar de smartphone vanaf deze wordt ingedrukt.
Anderzijds kan de toestand van de "built-in led" op de microcontroller gewijzigd worden door 2 knoppen op de smartphone.
Als laatste is het ook mogelijk om tekstberichten van de smartphone naar de pc te sturen, en omgekeerd.

## Arduino code:
De arduino code ziet er als volgt uit:
![image](https://github.com/jorenverdegem/Linefollower/assets/146443076/3d328238-ae5c-4d85-8f55-e7cfd50c9224)
![image](https://github.com/jorenverdegem/Linefollower/assets/146443076/5210d55d-0bfa-46ca-a331-b6037c6f910f)
Als eerste valt op dat we gebruik maken van de library "SoftwareSerial.h". Deze zorgt ervoor dat we een tweede softwarematige seriële monitor kunnen aanmaken, die wordt gebruikt door de smarthphone.
Als we kijken naar de eerste "if" structuur in de "void loop()" functie zien we dat de data wordt ingelezen van de seriële monitor van de smartphone, en wordt geschreven naar de seriële monitor van de computer.
Het omgekeerde gebeurd in de tweede "if" structuur. Op deze manier kunnen we al in twee richtingen berichten zenden.

In de derde "if" structuur wordt gezocht naar een '0' of een '1' in de data die binnenkomt vanaf de gsm. Dit is wat de knop op de gsm zal doorsturen als we de LED op de microcontroller willen laten branden.

Als laatste is ook een interruptfunctie toegevoegd met een debouncefunctie om de knop aan de microcontroller uit te lezen, en vervolgens een boodschap naar de gsm te sturen.
Dit principe kwam al eerder terug in de "Proof of concepts: interrupt".


## Elektronisch schema
Het elektronisch schema voor deze schakeling ziet er als volgt uit:
![image](https://github.com/jorenverdegem/Linefollower/assets/146443076/910bb865-b076-4bf6-bdc9-cbb8f9b517d8)
Merk op dat de RX van de bluetoothmodule niet rechtsreeks verbonden is met de TX van de microcontroller! Dit is belangrijk aangezien de HC-05 Bluetoothmodule met 3.3V signalen verwacht.
De arduino stuurt signalen van 5V. Daarom maken we een spanningsdeler met behulp van 2 weerstanden zodat we de 5V een stuk kunnen reduceren.

## Testresultaten
Op de smartphone ziet de seriële monitor er als volgt uit:
![370057969_310741495226934_2358127417559545938_n](https://github.com/jorenverdegem/Linefollower/assets/146443076/50d061e7-0ff6-4584-aff7-92415bef4b09)
Onderaan zijn de knoppen "on" en "off" te zien. Deze werden ingedrukt en verstuurden een '1' en een '0'. De LED aan de microcontroller ging effectief aan en uit wanneer op de corresponderende knoppen werd gedrukt.
Vervolgens is op de knop aan de microcontroller gedrukt. Hier ontvingen we correct het bericht "De knop is ingedrukt!". Als laatste is via de seriële monitor van de computer nog een testbericht gestuurd naar de gsm.
Hierop is het antwoord "test van gsm naar pc" verstuurd. Dit zien we dan ook verschijnen op seriële monitor van de computer:
![image](https://github.com/jorenverdegem/Linefollower/assets/146443076/aa822694-4b98-44ba-af3d-91ef5f1d90dc)

Als laatste is ook op de foto te zien dat de baudrate van onze seriële monitor is ingesteld op 9600 baud. Dit is belangrijk aangezien we dezelfde keuze hebben gemaakt in de arduinocode. Deze moeten overeenkomen!
