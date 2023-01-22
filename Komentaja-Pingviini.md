# Komentaja Pingviini

Aloitin lataamalla micro editorin kirjoittamalla terminaaliin komennon 

    curl https://getmic.ro | bash
    
Seuraavaksi asensin lshw työkalun saadakseni enemmän tietoa virtuaalikoneestani komennolla 

    $ sudo apt-get install lshw


 ![Add file: Upload](hardware.PNG)


Kuten analyysistä näkyy host koneessani on prossuna i5-11400F sekä annoin virtuaalikoneeseen 2 gigaa muistia 

## Komentoriviohjelmien lataus

Seuraavaksi latasin kolme hyödyllistä komentoriviohjelmaa käyttämällä komentoa 

    $ sudo apt install cmatrix figlet fortune
    
Ensimmäinen ohjelma, cmatrix, luo komentoriville leffoista tutun matrix animation

![image](https://user-images.githubusercontent.com/112076377/213911112-70dcf4a4-7e0a-43a5-9acf-0a7b9f432e7e.png)

Toinen ohjelma figlet luo kirjoittamastasi tekstistä ASCII taidetta!

![image](https://user-images.githubusercontent.com/112076377/213911174-35fea14a-70ef-44cd-a324-7a6f3ebd4c7d.png)

Kolmas ohjelma fortune tulostaa komentokehotteeseen satunnaisesti valitun vitsin tai opettavaisen viestin

![image](https://user-images.githubusercontent.com/112076377/213911348-418cbc23-a5db-4316-817a-dff4ea7b6ad6.png)


    
## Tärkeät kansiot

Ensimmäinen tärkeä kansio on root, jonka sisällä kaikki tiedostot ovat. Roottiin pääsin kirjoittamalla komentokehotteeseen 

    cd /
    
Oma roottini näyttää tältä. 

![Add file: Upload](root.PNG)

Seuraavaksi siirryin rootista home kansioon

    cd home
       
Home kansiossa ovat kaikki käyttäjät. Omassa virtuaalikoneessa siellä on vain oma käyttäjäni, koska en ole tehnyt enempää käyttäjiä 

![image](https://user-images.githubusercontent.com/112076377/213910637-8a98b17b-53f0-47b4-8092-15be94cf0b28.png)

Seuraava tärkeä kansio on home kansion sisällä olevien käyttäjien omat kansiot. Käyttäjien omat kansiot ovat ainoa paikka johon he voivat tallentaa tietoa 

    cd lassiv
    
Omassa tapauksessani

![image](https://user-images.githubusercontent.com/112076377/213910717-ba2fead4-7796-49a4-be91-df2a4ecf852f.png)

Siirryin seuraavaksi katsomaan kaikkia virtuaalikoneeni asetuksia root kansiossa olevasta etc kansiosta.

    cd /

    cd etc
    
![image](https://user-images.githubusercontent.com/112076377/213910910-b542a00c-cf65-4ed1-b742-356b4d7a1495.png)

Oma etc hakemistoni näytti tältä. Hakemistoon tulee lisää tietoa kun työskennellään ohjelmistoilla, jotka tallentavat omia asetuksia koneelle

Seuraava kansio, media, löytyy root kansion alta. Mediassa näkyy jos koneeseen on liittänyt esim. USB-tikkuja tai levykkeitä.

    cd /

    cd media
    
Oma media kansioni oli tyhjä, koska koneeseeni ei ole liitetty mm. USB-tikkuja

Viimeinen tärkeä kansio on var/log, jonne pääsee reittiä:

    cd /
    
    cd var/log
    
Logiin tallentuu koko järjestelmän log-tiedostot eli tekstitiedostoja eri järjestelmien tietyistä tapahtumista aikaleimoineen. Esim error tiedostot menevät tänne.

![image](https://user-images.githubusercontent.com/112076377/213911779-2042b270-e51a-4fca-9c8a-7048985d1890.png)

## Grep - komento

Grep - komentoa käytetään terminaalissa hakutyökaluna. Jotta sain testattua Grepin käyttöä täytin osaan aikaisemman harjoituksen /harjoitus/days/ kansioista tekstitiedostoilla. 

    cd sunday
    
    nano horse 
    
Hyödyllisistä grep komennoista ensimmäinen on 

    grep -R 'hakusana' .
    
Jolla voi hakea nykyisen kansion sekä sen alikansioiden sisältä tietyllä hakusanalla.

![image](https://user-images.githubusercontent.com/112076377/213912498-a8066da8-8517-4ece-8f5b-ef2533a30a95.png)

Grepillä voi myös tarkastella tarkemmin tiettyä kansiota ja löytyykö sen sisältä tietoa hakusanalla.

    grep 'hakusana' tiedostosijainti

![image](https://user-images.githubusercontent.com/112076377/213912596-cd62d552-4adf-4d9d-9359-54b2f81bfcd6.png)

Viimeinen hankalampi mutta selvästi hyödyllisempi komento 

    grep -r -i 'KALA' ~/harjoitus/days/
    
-r tarkastaa läpi kaikki kansiossa ja sen alikansioissa olevat tiedostot. -i ei välitä isoista ja pienistä kirjaimista. 

![image](https://user-images.githubusercontent.com/112076377/213913061-3fea2290-57aa-4f95-ba97-9eace5a276f8.png)
