# start/stop interrupt proof of concept
Om de werking van een start/stop interrupt te demonstreren op een arduino, waarin softwarematig gezorgd is voor een debounce van de schakelaar, is de volgende code geschreven:

![image (1)](https://github.com/jorenverdegem/Linefollower/assets/146443076/65a76b2e-55eb-4801-8ad1-eb73e2806f72)

De code werkt als volgt: als de schakelaar wordt ingedrukt waarmee men een start of stop signaal wilt genereren, zal via de "attachInterrupt" functie de loop hardwarematig onderbroken worden. Er hoeft dus niet telkens gepolled worden in de software om te kijken of de knop al dan niet is ingedrukt.
Als de intterupt wordt getriggerd wordt de functie "void interrupt()" uitgevoerd. Hierin wordt ter demonstratie de toestand van een led gewijzigd. Dit kan uiteraard vervangen worden door een start/stop signaal.

In deze interrupt zorgt de "millis()" functie er verder voor dat er geen debouncing kan optreden bij het indrukken van de schakelaar. De interrupt moet 100 ms actief zijn alvorens de functie effectief wordt uitgevoerd. Als ons knop dus even zou trillen, zal de functie geen meerdere keren worden uitgevoerd.

Vb: de knop trilt 3x met daartussen telkens 10 ms -> de functie zal maar 1x worden uitgevoerd aangezien de "if" functie zal zorgen voor een kleine delay.

Het elektronisch schema voor deze schakeling ziet er als volgt uit:

![image](https://github.com/jorenverdegem/Linefollower/assets/146443076/d832adc4-6d47-4fa8-82ad-2db1a4c94fd1)
