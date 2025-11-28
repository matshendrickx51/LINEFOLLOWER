
# Sensoren proof of concept

minimale hard- en software die aantoont dat minimaal 6 sensoren onafhankelijk van elkaar kunnen uitgelezen worden (geen calibratie, normalisatie of interpolatie). Hierbij moet een zo groot mogelijk bereik van de AD converter benut worden (indien van toepassing).
Hiervoor wordt de QTR-8A gebruikt, waarbij de laatste 2 sensoren van de printplaat worden afgebroken.

## Arduino code:

De arduino code ziet er als volgt uit:

![image (9)](https://github.com/jorenverdegem/Linefollower/assets/146443076/1854f7f8-8e9f-4573-ba13-e1ece4c80f97)

Hierbij maken we gebruik van de QTRSensors.h library. Deze maakt het mogelijk om de sensor evenvoudig te configureren en de waardes uit te lezen.
Vervolgens worden deze 6 sensorwaardes naast elkaar geprint op de seriële monitor. Het resultaat ziet er als volgt uit:

![image (10)](https://github.com/jorenverdegem/Linefollower/assets/146443076/606f8898-ff5f-426d-a106-e5160559ba22)

## Elektronisch schema:

Een elektronisch schema is bij deze schakeling overbodig, aangezien de 6 analoge outputs van de sensoren gewoon moeten verbonden worden met de 6 analoge inputs van de arduino.
Verder moet de sensor enkel nog gevoed worden met 5V, en moet ook de gnd worden verbonden.

![QTR](https://github.com/jorenverdegem/Linefollower/assets/146443076/c9f828be-077a-4a67-9423-de6e769040ee)
