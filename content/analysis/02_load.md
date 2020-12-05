---
Title: Load
Description: Analysis of loadtimes
---

Load
==========================
I denna rapport analyseras 3 olika hemsidors laddtider samt några av de förbättringsåtgärder de nyttjar.

Urval
--------------------------
Jag hade två krav när det kom till val av hemsidor. Det ska vara en hemsida jag tidigare är bekant med och hemsidans huvudsyfte ska vara att förmedla information.

MDN: Den officiella Mozilla-webbplatsen för dokumentation av webbstandarder. [1] [skärmdump](../assets/img/mdn.png)

JKN: En hemsida för en advokatbyrå. [2] [skärmdump](../assets/img/jkn.png)

Dbwebb: Hemsida med kursmaterial relevant till Dbwebb-kurser. [3] [skärmdump](../assets/img/dbwebb.png)

Metod
--------------------------
Som verktyg använde jag mig av Pagespeed Insights [4] och chromes egna utvecklarverktyg för att mäta hemsidornas prestanda. Sedan använde jag google sheets för att dokumentera resultaten.


Resultat
--------------------------
[Kalkylark](https://docs.google.com/spreadsheets/d/15m3yCmMMwUFqgSfkhe3uoDkbK3IUiQtN1mJGVTpIicg/edit?usp=sharing)


Analys
--------------------------
Tittar vi på poängen sidorna fick i mätningarna kan vi se att att alla sidorna var väldigt nära varandra när det kom till desktop-varianterna där dbwebb var snabbast med 97 poäng och JKN segast med 93 poäng. Tittar vi dock på mobilpoängen är det större skillnad. Allra segast var, igen, JKN med 69 poäng och snabbast var, igen, dbwebb med 92 poäng. Varför är då dbwebb mycket snabbare än de andra sidorna? Det kan delvis förklaras genom att titta på en för alla sidor gemensam förbättringsåtgärd: Undvikande av blockering av renderingen. På desktopsidorna är resultaten väldigt nära varandra där den enda skillnaden finns på MDN där renderingen blockeras i 10ms till skillnad från 0ms hos de andra. Däremot är det stor skillnad när det kommer till blockering av renderingen i mobilsidorna. Där blockerar dbwebb endast renderingen i 40ms till skillnad från de andra två som blockerar mer än dubbelt så länge med 110ms för MDN och 150ms för JKN.

Kollar man på poängen är dbwebb den uppenbara vinnaren, både på mobil och desktop. Ska man därefter rangordna de andra två sidorn kommer MDN på andra plats och JKN på tredje. Anledningen till att dbwebb vinner har delvis att göra med det tidigare nämnda angående blockering av renderingen men påverkas säkert en hel del av att Dbwebb inte skickar lika mycket data som de andra två. Anledningen till att JKN är allra segast har säkerligen att göra med sidans användning av stora högkvalitetsbilder som bakgrunder vilket leder till mer data som skickas mellan clienten och servern.

När det kommer till desktop-sidorna tycker jag att alla är snabba nog, där laddas alla sidor in helt inom 1.5 sekund. Jag uppfattar hemsidor som tar mer än 3 sekunder att ladda klart som sega. På mobilen misslyckas både JKN och MDN med att uppfylla mina krav för vad en snabb hemsida innebär. Mdn tar 5.1 sekunder på sig att ladda klart och JKN tar hela 5,6 sekunder. På gränsen ligger dock dbwebb med exakt 3 sekunder.

Alla tre sidor kan förbättras. När det kommer till JKN skulle man kunna vänta med att läsa in sidans andra bakgrundsbild som ligger "below the fold". Mdn kan förbättras genom att undvika blockeringen av hemsidans rendering samt förbättra deras svarstid på servern. Dbwebb behöver minst förbättringar men skulle eventuellt kunna förminska storleken på sidans bilder i mobilläget.


Referenser
--------------------------
* https://developer.mozilla.org/en-US/ [1]
* https://dbwebb.se/ [2]
* https://jkn.se/ [3]
* https://developers.google.com/speed/pagespeed/insights/?hl=sv [4]

Skrivet av Daniel Lundgren
