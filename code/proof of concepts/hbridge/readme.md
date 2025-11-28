# H-Bridge proof of concept

Minimale hard- & software die aantoont dat 2 motoren onafhankelijk van elkaar kunnen draaien, en (traploos) regelbaar zijn in snelheid en draairichting.
Hiervoor wordt gebruik gemaakt van 2 "Mini Micro Metal Gear Motor 6V DC - Ratio 30:1" motoren en als H-brug gebruiken we de "DRV8833 Dual Motor Driver Carrier".

## Functionaliteit:

Het geschreven programma zal in een loop demonstreren hoe de motoren geleidelijk aan versnellen tot het maximale snelheid, en vervolgens weer vertragen naar 0. 
Vervolgens wordt gedemonstreerd dat ze ook in tegengestelde richting kunnen draaien, en ook afzonderlijk van elkaar een andere draairichting kunnen aannemen.

## Arduinocode:

![image (11)](https://github.com/jorenverdegem/Linefollower/assets/146443076/80188d47-8410-4344-a31c-98d5c9f91798)
![image (12)](https://github.com/jorenverdegem/Linefollower/assets/146443076/14e6c77a-284e-45dd-8481-d3c1e941dee8)
![image (13)](https://github.com/jorenverdegem/Linefollower/assets/146443076/6568e12a-6885-4667-9005-2d075a1f8795)

In de setup worden de pinnen die verbonden zijn met de H-brug als OUTPUT geconfigureerd en worden de motoren uitgezet.
Vervolgens begint te "void loop" functie waarin verschillende zaken gebeuren:
  1. De motoren gaan van stilstand geleidelijk aan naar hun maximale snelheid.
  2. De motoren blijven 2 seconden aan hun maximale snelheid draaien.
  3. De motoren vertragen van hun maximale snelheid naar stilstand.
  4. De motoren blijven 2 seconden uit.
  5. De maximale snelheid in tegengestelde draairichting worden op beide motoren gedemonstreerd voor 2 seconden.
  6. De motoren blijven 2 seconden uit.
  7. De motoren draaien 2 seconden aan hun maximale snelheid, maar beide met een andere draairichting.
  8. De motoren blijven 1 seconde uit.
  9. de motoren draaien 2 seconden aan hun maximale snelhied, maar nu beide in de andere richting dan de vorige stap.
  10. De motoren blijven 1 seconde uit

Vervolgens zijn nog 3 andere functies in gemaakt. Deze zullen ervoor zorgen dat we via de "spin_and_wait" functie overzichtelijk de snelheid kunnen geven aan de 2 motoren.
Ook wordt hier duidelijk gemaakt dat de draairichting moet veranderen als we een negatieve waarde ingeven en wordt de snelheid geschreven naar de seriële monitor.

## Elektronisch schema:

Het elektronisch schema voor deze schakeling ziet er als volgt uit:
![Schema H-bruggen](https://github.com/jorenverdegem/Linefollower/assets/146443076/8cdba92c-be9d-4f57-b7a5-b351e24d55e4)

## Testresultaten:

Op de seriële monitor kunnen we mooi volgen welke snelheid de motoren op dit moment hebben aangenomen:
![image (14)](https://github.com/jorenverdegem/Linefollower/assets/146443076/3ee4517c-b8ee-47e8-b3b4-9d075595334a)
