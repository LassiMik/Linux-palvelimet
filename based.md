# h6 Based

Aloitin tehtävien teon klo 11:08 6.2

## x) Lue ja tiivistä 11:09
Luin kaksi Apachen palvelinohjelmointi-dokumenttia ja tiivistin ne pariin ranskalaiseen viivaan

Apache - Getting started [1]

- Dokumentti käy läpi perusasioita servereiden tominnasta ja servereiden perustamisesta
- Nettisivua varten tarvitsee oman DNS osoitteen eli esimerkiksi "www.example.com". DNS osoite viittaa IP osoitteeseen, jolla nettisivu on.
- Moni DNS osoite voi osoittaa samaan IP osoitteeseen sekä samalla fyysisellä serverillä voi olla monta eri nettiosoitetta käyttäen virtuaalisointia
- Apache palvelinta voi configuroida kirjoittamalla direktiivejä .conf tiedostoihin
- Jos palvelin kohtaa virhetilanteen siitä tulee loki apachen error.log tiedostoon. Error.log tiedostossa virhetilanteet sisältävät koodin, joka helpottaa ongelman korjaamisessa

Apache - Name-based Virtual Host Support [2]

- IP-based virtual hostit käyttävät yhteyden IP osoitetta päätelläkseen oikean sivun. Hostit vaativat erilliset omat IP osoitteensa.
- Name-based virtual hosting käyttää puolestaan DNS osoitteita kartoittaakseen oikeat DNS nimet oikeisiin IP osoitteisiin.
- Name-based virtual hostingin käyttöönottamiseksi sinun on luotava jokaiselle hostille lohko, jossa on vähintään ServerName-direktiivi sekä DocumentRoot-direktiivi. 
- Name-based virtual hosting on paljon nykyaikaisempi ja käytetympi kuin IP-based virtual hosting.

## a) Apachelle uusi etusivu 13:36

Nykyinen apachen etusivuni näyttää tältä:

![image](https://user-images.githubusercontent.com/112076377/216962014-4bdd7ae7-0852-4871-a3e9-1e832f976d22.png)










## Lähteet
[1] https://httpd.apache.org/docs/2.4/getting-started.html

[2] https://httpd.apache.org/docs/current/vhosts/name-based.html
