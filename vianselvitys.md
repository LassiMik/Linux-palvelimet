# h12 vianselvitys 5.3.2023 20:57

## Alkutilanne 20:59

Aloitin tehtävien tekemisen viimeisen kotiläksyn pohjalta, jossa pystytin toimivan djangon tuotantoasennuksen

Varmistin vielä, että kaikki toimii
![image](https://user-images.githubusercontent.com/112076377/222980407-49c62389-d3a6-44b6-beb4-6e12cdc9acd3.png)

![image](https://user-images.githubusercontent.com/112076377/222980524-644ba55b-a602-4bec-a235-c6834e14ea55.png)

## a) kirjoitusvirhe Python-tiedostossa 21:05

Aiheutin tahallisen kirjoitusvirheen settings.py tiedostoon

![image](https://user-images.githubusercontent.com/112076377/222980845-9e5e3a43-b42c-4922-84d6-b75994f87b91.png)

Päivitin muutokset palvelimelle käynnistämällä palvelimen uudestaan komennolla

    sudo systemctl restart apache2
    
Päivitin vielä nettisivun, joka vielä alussa toimi. 

![image](https://user-images.githubusercontent.com/112076377/222981017-d8db00d0-3b5f-42d6-8bfb-58481a23a1e7.png)

Aloitin ongelman ratkomisen kokeilemalla apachen omaa configtestiä

    /sbin/apache2ctl configtest

![image](https://user-images.githubusercontent.com/112076377/222981144-9129e3a4-510c-49f0-a78e-2ae90dd59890.png)

Configtesti palauttaa saman tuloksen, kuin toimiva palvelin, joten configtesti ei osaa tunnistaa että on edes mitään ongelmaa. 

Noudatin seuraavaksi sivuston antaman errorin ohjeita eli siirryin tarkastelemaan apachen errorlogeja

    sudo tail -F /var/log/apache2/error.log

![image](https://user-images.githubusercontent.com/112076377/222981112-8579539f-c892-4b77-b647-6c206b7bafcc.png)

Errorlogit osasivat paikantaa ongelman aiheuttajan

Korjasin ongelman siirtymällä testico kansion sisälle ja muuttamalla settings.py tiedoston sisällä olevan importin takaisin

![image](https://user-images.githubusercontent.com/112076377/222981475-c548a066-1aa1-4672-a50b-659a800b3162.png)

Käynnistin vielä palvelimen uudestaan 

    sudo systemctl restart apache2
    
![image](https://user-images.githubusercontent.com/112076377/222981689-29e13949-2edb-4998-bec5-2e22bcf5e391.png)

sivusto toimii.

## b) Django-projektikansio väärässä paikassa 21:50

Siirsin koko django projektikansion, jonka sisällä manage.py tiedosto on oman pääkäyttäjäni kotihakemistossa olevaan harjoitus kansioon. Käytin komentoa 

    mv testico/ /home/lassiv/harjoitus/
    
Ilman apachen päivitystä nettisivu antaa jo error viestiä

![image](https://user-images.githubusercontent.com/112076377/222982864-11e61888-9a5c-43fb-88fc-faa878ba71c7.png)

Ensimmäinen idea errorviestistä oli käydä katsomassa apachen accesslogit komennolla

    sudo tail -F /var/log/apache2/access.log
    
![image](https://user-images.githubusercontent.com/112076377/222983085-7af9aed5-578d-4027-ae7f-0ff5b604b452.png)

Joka ei suostunut tulostamaan mitään

Seuraavaksi kokeilin apachen configtestiä

    /sbin/apache2ctl configtest
    
![image](https://user-images.githubusercontent.com/112076377/222983192-748c085a-4481-4860-a86e-1814cbdd4b55.png)

Ei errorviestejä täälläkään.

Seuraavaksi tutkin apachen errorlogeja komennolla

    sudo tail -F /var/log/apache2/error.log

![image](https://user-images.githubusercontent.com/112076377/222983314-c6071fbf-05ea-48ce-b979-1c0b0c087a46.png)

Errorlogissa näkyy "client denied by server configuration: /home/lassiv/publicwsgi/testico"

Tulkitsen errorviestistä sen, että kyseessä olevan polun testico tiedostossa on määritetty, että kyseessä olevassa tiedostossa on määritetty, että hakuselaimella ei pääse näkymään, mitä tavoitellaan. 

Joka on omituista koska kyseistä polkua ei ole enää olemassa, koska siirsin testico tiedoston sijaintia.

![image](https://user-images.githubusercontent.com/112076377/222983394-89fbeb3e-ccee-489c-9655-9d94a38269f4.png)

Korjaan virheen siirtämällä harjoitus kansion sisällä olevan testico kansion takaisin vanhaan sijaintiinsa 

siirryin ensin kotihakemistoni harjoitus kansioon komennolla 

    cd 
    cd harjoitus
    
Jonka jälkeen siirsin mv komennolla testico kansion takaisin oikeaan sijaintiinsa

    mv testico/ /home/lassiv/publicwsgi/

Käynnistin vielä apachen uudestaan komennolla

    sudo systemctl restart apache2

![image](https://user-images.githubusercontent.com/112076377/222983807-f72dc9c4-9e19-42f0-8a63-c728ee071e91.png)

Siirron ja uudelleenkäynnistyksen jälkeen sivusto taas toimii normaalisti

sain b) kohdan valmiiksi 5.3.2023 22:37 ja jatkan tästä huomenna

## c) Projektikansiolla väärät oikeudet xx:xx





## Lähteet xx:xx

[1] https://www.cyberciti.biz/faq/mv-command-howto-move-folder-in-linux-terminal/
