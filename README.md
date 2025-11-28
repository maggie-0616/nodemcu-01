# Blink-system med Arduino

En kort och enkel guide till hur ett blinkande LED-system fungerar på en Arduino-mikrokontroller.

## Mikroprocessor som används

I detta projekt används microprocessorn **NodeMCU**, som bygger på mikrokontrollern **ESP8266**. NodeMCU kan programmeras med Arduino-kod och har flera digitala portar som gör den enkel att använda för nybörjare.

* För att ESP8266 ska funka så måste man kopiera en URL-kod:
```cpp
https://arduino.esp8266.com/stable/package_esp8266com_index.json
```
* Sedan trycker man på Arduino IDE (i vänstra hörnet uppe på MAC)->```Prefrences```-> klistra in URL-koden i rutan.
  
---


## Arduino – två basfunktioner

Arduino-program (sketcher) består alltid av två huvudfunktioner:

* ```setup()```
  Körs **en gång** när kortet startar. Här görs inställningar, t.ex. att ange vilka portar som är in- eller utgångar.

* ```loop()```
  Körs **om och om igen**, i en evig loop. Här skriver man programlogiken som ska upprepas.

## Portinitialisering

För att använda en digital port måste den först ställas in som antingen **INPUT** eller **OUTPUT**.
I detta projekt används den inbyggda LED:en (**LED_BUILTIN**), som är kopplad till en digital utgång.

```cpp
pinMode(LED_BUILTIN, OUTPUT);
```

Det betyder att porten ska skicka signaler (HIGH eller LOW) för att styra LED-lampan.
* För att välja port (input/outout) så trycker man på ```tools```->```port```-> Sen väljer du rätt port.

## Kod med enkla förklaringar

* För att hitta blink programmet i Arduine IDE så måste man gå in på ```file```-> ```examples```-> ```01.Basics```->```Blink```

```cpp
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);   // Gör LED-porten till en utgång
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // Tänd LED (sätt porten till HIGH)
  delay(1000);                      // Vänta 1 sekund
  digitalWrite(LED_BUILTIN, LOW);   // Släck LED (sätt porten till LOW)
  delay(1000);                      // Vänta 1 sekund
}
```

### Kort sammanfattning

* ```digitalWrite()``` styr portens nivå (HIGH = på, LOW = av).
* ```delay()``` pausar programmet i ett antal millisekunder.
* Programmet tänder och släcker LED-lampan med ett intervall på 1 sekund när nummret i parantesen är 1000 (millisekunder).
