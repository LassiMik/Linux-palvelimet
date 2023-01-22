# Komentaja Pingviini

Aloitin lataamalla micro editorin kirjoittamalla terminaaliin komennon 

    curl https://getmic.ro | bash
    
Seuraavaksi asensin lshw työkalun saadakseni enemmän tietoa virtuaalikoneestani komennolla 

    $ sudo apt-get install lshw


 ![Add file: Upload](hardware.PNG)


Kuten analyysistä näkyy host koneessani on prossuna i5-11400F sekä annoin virtuaalikoneeseen 2 gigaa muistia 

## Komentoriviohjelmien lataus

Seuraavaksi latasin kolme hyödyllistä komentoriviohjelmaa käyttämällä komentoa 

    $ sudo apt install cmatrix cowsay fortune
    
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
