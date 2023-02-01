# h5 Hello web 
Aloitin tehtävien teon 1.2.2022 klo 16:13

## x) Vapaavalintainen Indie Hackers -podcast

Tehtävää varten kuuntelin jakson [1] "Bootstrapping a leather supply business to $50k in sales" - Jared Maddern, Beamhouse Leather 

 - Haastateltavana Jared Maddern, Beamhouse Leather perustaja.
 - Beamhouse Leather jälleenmyy nahkaa sekä harrastajille sekä muille yrityksille
 - Jared Maddern kiinnoistui nahan jälleenmyynnistä aloitettuaan harrastuksen nahan askartelusta koronaepidemian alussa 2019
 - Jared tilasi nahkaa Ebaysta sekä työkaluja ebaysta ja amazonista
 - huhtikuussa 2020 tilasi ensimmäisen kokonaisen nahkataljansa
 - Harrastuksen kehittyessä kiinnostui enemmän nahkan jälleenmyynnistä, koska huomasi että muutkin olivat aloittaneet saman harrastuksen koronan takia
 - Aloitti myymään nahkaa sekä muita nahkatarvikkeita etsyssä, koska etsyn tekeminen oli nopeaa ja siellä oli valmiiksi paljon asiakkaita. Etsyssä oli myös vähemmän kilpailua, kuin omat nettisivut tehneillä yrittäjillä tai ebayssä
 
## a) Apachen esimerkkisivun vaihto 16:39

Korvasin apachen tekemän esimerkkisivun komennolla

    echo Moi | sudo tee var/www/html/index.html

Joka näyttää selaimessa tältä

![image](https://user-images.githubusercontent.com/112076377/216075704-edd29fd6-a69d-498c-8f01-cb83140060bc.png)

## b) käyttäjien kotisivut 16:54

Kertasin tunnilla käytyä aihetta apachen servereistä [2]

Menin käyttäjäkohtaiseen public_html kansioon komennolla

    cd home/lassiv/public_html
    
Ja tein sinne esimerkki html sivun hello.html komennolla

    nano hello.html
    
Joka näytti selaimessa tältä 

![image](https://user-images.githubusercontent.com/112076377/216085164-31e4e4ae-0fe9-4827-80bd-d849a861e457.png)

## c) uuden käyttäjän luonti 17:29

Loin uuden testikäyttäjän komennolla 

    sudo adduser lassivar
   
Jonka jälkeen lisäsin "real name" kohtaan testikäyttäjä minun käyttäjälleni. loput kohdat jätin tyhjäksi entteriä painamalla.

![image](https://user-images.githubusercontent.com/112076377/216087333-79abbf01-6fa9-4664-8302-dc83ac888274.png)

Kirjauduin ulos pääkäyttäjältäni ja sisään uudelle käyttäjälleni. Tämän jälkeen tietokone oli osannut tehdä käyttäjälleni omat kansiot, kuten public_html.
Kävin vielä kokeilemassa toimiihan uuden käyttäjän kotisivut

![image](https://user-images.githubusercontent.com/112076377/216089129-7eee7b5e-96d4-4455-b0f8-4c864d31a467.png)

## d) validi html5 sivu 17:40

Aloitin html sivun tekemisen muokkaamalla jo aikaisemmassa tehtävässä tekemääni html sivua pääkäyttäjäni public_html kansioon.
Siirryin kansioon komennolla

    cd /home/lassiv/public_html/
    
Kun olin hakemistossa kirjoitin komennon 

    nano hello.html
    
Jotta pääsin muokkaamaan / tekemään tiedoston hello.html. 

Tältä näytti valmis tiedosto:

![image](https://user-images.githubusercontent.com/112076377/216093033-f8b522c6-2422-4ae1-92b6-1d512c7d7208.png)

Tarkastin vielä miltä se näyttää selaimen kautta

![image](https://user-images.githubusercontent.com/112076377/216093421-aab17bd3-a692-4453-aa7b-01896094e29e.png)

## Loppusanat

Tehtävät sain valmiiksi 17:51

Eniten vaikeuksia tehtävissä tuotti b) kohta, käyttäjien kotisivujen luonti, koska en aluksi ymmärtänyt mitä siinä haettiin



## Lähteet 

[1] https://indiebites.com/74

[2] https://linuxzoo.net/page/tut_eapache.html

