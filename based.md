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

Poistin vanhan pääsivuni käyttäen komentoa

    rm index.html

ja tein uuden html tiedoston index.html käyttämällä komentoa 

    nano index.html
    
Jonka jälkeen annoin kaikille käyttäjille oikeudet editoida tiedostoa komennolla

    sudo chmod -R 777 /home/lassiv/public_site/

Käynnistin sen jälkeen apachen uudestaan komennolla

    sudo service apache2 restart

Uusi html sivuni toimii ja sitä voi editoida ilman sudo oikeuksia

![image](https://user-images.githubusercontent.com/112076377/216968104-59ce6ed6-21ed-448b-bf94-f918d3d4bcf8.png)

![image](https://user-images.githubusercontent.com/112076377/216968597-d748c475-9c2b-40df-b66e-ec8575e08a26.png)


## b) apachen asetustiedostoon kirjoitusvirhe 14:17

Siirryin apachen config tiedostoihin komennolla 

    cd /etc/apache2/sites-available/

Jonka jälkeen editoin config tiedostoani newdefault.conf komennolla

    sudo nano newdefault.conf 

Ja poistin sieltä yhden closing tagin

![image](https://user-images.githubusercontent.com/112076377/216969609-bec74a6b-2e62-47ce-a014-23abd9f6092d.png)

Käynnistin apache serverini uudestaan komennolla 

    sudo service apache2 restart
    
Jonka jälkeen sain error viestin

![image](https://user-images.githubusercontent.com/112076377/216969999-d4577fff-4ded-42f9-9753-4a29665d4258.png)

Seuraavaksi kokeilin selvittää virheen käyttämällä komentoa

    sudo apache2ctl configtest
    
![image](https://user-images.githubusercontent.com/112076377/216971023-26f9547e-0d6d-4815-af8e-d4e79feb55a4.png)


## Lähteet
[1] https://httpd.apache.org/docs/2.4/getting-started.html

[2] https://httpd.apache.org/docs/current/vhosts/name-based.html

[3] https://stackoverflow.com/questions/49944942/ls-cannot-open-directory-permission-denied
