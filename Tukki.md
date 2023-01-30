# Tukki

Aloitin tehtävien teon 12:31 30.1.2023

## Hacker news [1]
  Valitsin tarkasteluun linux aiheisen artikkelin "An interactive cheatsheet tool for the command-line"
  - Tarkoitus nopeuttaa pitkien komentokehote scriptien kirjoittamista ja syntaksin muistamista
  - Voit tehdä omia cheatsheettejä tai käyttää valmiita ohjelman mukana tulevia
  - Kaikki cheatsheetissä olevat scriptit on myös tehtävissä ilman cheatsheettiä
  - Linuxin kokeneemmat kommentoijat pitävät cheatsheettiä turhana, koska tuntevat linuxin komentokehotteen syntaksin kuin omat taskunsa
  
sain valmiiksi x) kohdan 12:50 
## a) Tukki 12:51
### syslog
 siirryin var/log/ kansioon juuri kansiosta komennolla
 
    cd var/log
 
 Jonka jälkeen tarkastelin tiedostoa syslog komennolla
 
    sudo cat syslog

![image](https://user-images.githubusercontent.com/112076377/215466688-23240e5d-e161-4995-8f4f-74929716dc53.png)

 Esimerkkirivi tulostetusta tiedosta edellisellä komennolla
 
Syslog siis tulostaa näytölle aikajanassa kaikki tapahtumat joille ei ole omaa lokia.
Esimerkkitulostuksessa poimin yhden rivin jossa näkyy tapahtuma, kun kirjauduin virtuaalitietokoneelle. 
Tulostuksessa näkyy paikallinen aika (kirjauduin 13:33 tietokoneelle), sekä päivämäärä 30.1
Kellonajan ja päivämäärän jälkeen tulostuu virtuaalikoneen nimi "foo".
Foon jälkeen näkyy network managerin antama koodi 458 joka kertoo inffoa tapahtumasta "agent registered"

### auth.log
Seuraava tiedosto jota tarkastelen on auth.log 
Tulostin auth.log sisällön samasta hakemistosta, jossa edellisen tehtävän komennolla

    sudo cat auth.log
    
![image](https://user-images.githubusercontent.com/112076377/215468377-833af958-9f1a-4169-b73f-6d79c290c657.png)

Aikaisemmassa kohdassa tarkastelin syslogia jossa näkyi, kun joku mystinen "agentti" kirjautui omalle foo koneelleni
auth.log kertoo tarkempaa tietoa kirjautumistapahtumasta. Tulostuksessa näkyy päivämäärä sekä aika tapahtumalle. "systemd-logind" viittaa selvästi kirjautumiseen sekä koneen nimi "foo" edessä kertoo että virtuaalikoneelleni kirjauduttiin klo 13:33 tänään 30.1.
"New session 2 of user lassiv" kertoo että omalle "lassiv" käyttäjälleni kirjauduttiin onnistuneesti


### apache2/access.log
Yritin seuraavaksi tarkastella apache2 kansion sisällä olevaa access.log tiedostoa, mutta en onnistunut. Virhe korjaantui kun sammutin apache2 serverin ja käynnistin uudestaan. Katselin access.log tiedoston sisältöä komennolla 

    sudo tail /var/log/apache2/access.log
    
 ![image](https://user-images.githubusercontent.com/112076377/215476734-d4befc0e-317c-435b-83e9-38745614fc3e.png)

access.log tiedostossa ensimmäisenä tulee ip osoite, josta pyyntö sivustolle on tehty. Tapauksessa, jossa sivustomme on localhostilla ip osoite on 127.0.0.1.
Seuraavaksi access.log näyttää päivämäärän sekä kellonajan milloin pyyntö on tehty. Kello näkyy suomen aikaa normaalissa ajassa sekä perässä on vielä aikavyöhyketunniste (+0200), jos joku haluaa kääntää suomen ajan omalle aikavyöhykkeelleen.

Aikavyöhykkeen jälkeen

## b) Aiheuta 14:03 

### syslog

En saanut tahallani aiheutettua virheilmoitusta syslog tiedostoon. Onnistuin kuitenkin kirjoittamaan sinne komennolla 

    logger "System rebooted for hard disk upgrade"

![image](https://user-images.githubusercontent.com/112076377/215474776-c8b8f8eb-a97c-41b9-b01a-679f1f5570eb.png)

Tiedostossa syslog näkyy kellonaika sekä päivämäärä kun komento kirjoitettiin. Komennon kirjoittaja näkyy myös. Logger komennon jälkeinen viesti näkyy käyttäjänimen jälkeen


### auth.log

Kävin aikaisemmin läpi miten onnistunut kirjautuminen näkyi tiedostossa auth.log 

Aiheutin tahallisen sudo komennon virheen kirjoittamalla salasanani väärin 
![image](https://user-images.githubusercontent.com/112076377/215472995-c20162a4-e87f-4401-a790-44b35c12c959.png)

Tuttuun tapaan auth.log tulostaa tapahtuman kellonajan sekä päivämäärän rivin alkuun. Sen jälkeen komento antaa virheilmoituksen "authentication failure" koska ei pysty tunnistamaan minua väärällä salasanalla. auth.log myös tulostaa käyttäjän nimen joka yritti käyttää sudoa


## Lähteet
- [1] https://news.ycombinator.com/item?id=210321362  
