# Tukki

Aloitin tehtävien teon 12:31 30.1.2023

## Hacker news [1]
  Valitsin tarkasteluun linux aiheisen artikkelin "An interactive cheatsheet tool for the command-line"
  - Tarkoitus nopeuttaa pitkien komentokehote scriptien kirjoittamista ja syntaksin muistamista
  - Voit tehdä omia cheatsheettejä tai käyttää valmiita ohjelman mukana tulevia
  - Kaikki cheatsheetissä olevat scriptit on myös tehtävissä ilman cheatsheettiä
  - Linuxin kokeneemmat kommentoijat pitävät cheatsheettiä turhana, koska tuntevat linuxin komentokehotteen syntaksin kuin omat taskunsa
  
sain valmiiksi x) kohdan 12:50 
## a) tukki 12:51
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

Seuraava tiedosto jota tarkastelen on auth.log 
Tulostin auth.log sisällön samasta hakemistosta, jossa edellisen tehtävän komennolla

    sudo cat auth.log
    
![image](https://user-images.githubusercontent.com/112076377/215468377-833af958-9f1a-4169-b73f-6d79c290c657.png)

Aikaisemmassa kohdassa tarkastelin syslogia jossa näkyi, kun joku mystinen "agentti" kirjautui omalle foo koneelleni
auth.log kertoo tarkempaa tietoa kirjautumistapahtumasta. Tulostuksessa näkyy päivämäärä sekä aika tapahtumalle. "systemd-logind" viittaa selvästi kirjautumiseen sekä koneen nimi "foo" edessä kertoo että virtuaalikoneelleni kirjauduttiin klo 13:33 tänään 30.1.
"New session 2 of user lassiv" kertoo että omalle "lassiv" käyttäjälleni kirjauduttiin onnistuneesti


## Aiheuta 14:03 

Kävin aikaisemmin läpi miten onnistunut kirjautuminen näkyi tiedostossa auth.log 

Aiheutin tahallisen sudo komennon virheen kirjoittamalla salasanani väärin 
![image](https://user-images.githubusercontent.com/112076377/215472995-c20162a4-e87f-4401-a790-44b35c12c959.png)



## Lähteet
- [1] https://news.ycombinator.com/item?id=210321362  
