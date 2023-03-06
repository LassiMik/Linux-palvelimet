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

## c) Projektikansiolla väärät oikeudet 6.3.2023 10:51

Tarkastin aluksi projektikansioni oikeudet komennolla

    ls -l
    
![image](https://user-images.githubusercontent.com/112076377/223062416-fac4c05d-14d6-4382-a93c-54944c989cfa.png)

Muutin projektikansion oikeuksia komennolla

    chmod ugo-rwx testico/
    
![image](https://user-images.githubusercontent.com/112076377/223063016-60526d2b-bbd2-469c-a48f-1990b8586ec3.png)

Muutoksen jälkeen sivuston admin näkymä palauttaa forbidden 

![image](https://user-images.githubusercontent.com/112076377/223063318-a1fbeef5-23ea-4adf-a158-ab7021ce4354.png)

Aloitin ratkomaan ongelmaa ensimmäiseksi käymällä tarkastelemassa apachen errorlogeja

    sudo tail -F /var/log/apache2/error.log

![image](https://user-images.githubusercontent.com/112076377/223064139-7e2e3c53-16ea-44c3-9fe4-529f7e2ed3d6.png)

Apachen errorlogit eivät tulostaneet mitään

Seuraavaksi yritin siirtyä projektikansioon komennolla

    cd testico/
    
![image](https://user-images.githubusercontent.com/112076377/223064563-4038b6f8-5adb-4ed4-8f67-7478d403d75b.png)

En pystynyt siirtymään projektikansioon, koska sudokäyttäjälläni ei ole tarpeeksi oikeuksia

Korjasin oikeuksiin liittyvät ongelmat antamalla aikaisemmin poistamani oikeudet takaisin komennolla

    chmod +rwx testico/
    
![image](https://user-images.githubusercontent.com/112076377/223066201-1dcd972f-c028-409a-aca5-b74148d95924.png)

En tehnyt missään vaiheessa tätä tehtävää pythonin migraatioita tai uudelleenkäynnistänyt apachea ja nyt sivu taas toimii normaaliin tapaan

![image](https://user-images.githubusercontent.com/112076377/223066519-13657268-4580-4541-bb07-1c9a98efe191.png)

## d) Kirjoitusvirhe Apachen asetustiedostossa 11:12

Siirryin editoimaan conf tiedostoa komennolla

    sudoedit /etc/apache2/sites-available/lassico.conf
    
![image](https://user-images.githubusercontent.com/112076377/223067326-d61d6aed-0187-4d12-a913-1a4126970427.png)

Yritin käynnistää apachea uudestaan komennolla 

    sudo systemctl restart apache2
    
![image](https://user-images.githubusercontent.com/112076377/223069107-096ca077-7749-4217-964a-66635f6d63eb.png)

Apache ei suostu edes käynnistymään viallisella config tiedostolla

Kävin seuraavaksi vilkaisemassa apachen configtestiä

    /sbin/apache2ctl configtest
    
![image](https://user-images.githubusercontent.com/112076377/223068659-051eb235-0edf-4026-96dc-1840c2930220.png)

Configtest osasi suoraan kertoa ongelman alkuperän

Korjasin ongelman sudoeditoimalla ongelman config tiedostossa.

Apachen uudelleenkäynnistämisen jälkeen sivusto taas toimii normaalisti

## e) Apachen WSGI-moduli puuttuu 11:25

Aloitin poistamalla wsgi moduulin komennolla

    sudo apt-get purge libapache2-mod-wsgi-py3

Käynnistin vielä palvelimen uudestaan komennolla

    sudo systemctl restart apache2

![image](https://user-images.githubusercontent.com/112076377/223071212-6ea22e6a-6dd9-4ee7-9cd8-36b2c6acc748.png)

Uudelleenkäynnistys tulosti aikaisemmasta tehtävästä tutun errorviestin

Kävin seuraavaksi configtestaamassa 

    /sbin/apache2ctl configtest

![image](https://user-images.githubusercontent.com/112076377/223071619-80fcce30-789b-4c4a-a478-1fad9f0081f8.png)

Configtest valittaa väärästä komennosta "WSGIDaemonProcess", joka voi olla väärinkirjoitettu tai jota ei ole ladattu. 

Configtest siis osasi paikantaa ongelman syyn

Korjaan ongelman lataamalla poistamani moduulin takaisin komennolla

    sudo apt-get -y install libapache2-mod-wsgi-py3

Jonka jälkeen käynnistin vielä palvelimen uudestaan ja tarkastelin configtestiä

![image](https://user-images.githubusercontent.com/112076377/223072730-be0bdfd8-df55-4d21-8826-df4653ccf2f4.png)

## f) Väärät domain-nimet ALLOWED_HOSTS-kohdassa 11:38

Aloitin vaihtamalla domain nimen ALLOWED_HOST-kohtaan projektin settings.py tiedostossa

    micro testico/testico/settings.py

![image](https://user-images.githubusercontent.com/112076377/223073497-fbde9a79-eba3-4f6b-96ad-97482d278082.png)

Käynnistin apachen uudestaan sekä tein migraatiot

    ./manage.py makemigrations
    ./manage.py migrate
    sudo systemctl restart apache2

![image](https://user-images.githubusercontent.com/112076377/223074526-c32509a2-ec14-44d9-a5fe-beac278a5524.png)

Tarkastelin kaikki apachen logit läpi komennolla

    sudo tail -F /var/log/apache2/

Ainoat tapahtumat mitä logeihin kirjattiin errorista oli get pyynnöt, jotka ei ongelmanratkaisussa auttaneet.

Apachen configtest palautti "syntax ok" eli ei sielläkään virheitä

Kävin tässä välissä settings.py tiedostossa vaihtamassa debug tilan takaisin päälle 

![image](https://user-images.githubusercontent.com/112076377/223076192-7ba74ea0-4e8a-4352-ac09-914c8f2b27a0.png)












## Lähteet xx:xx

[1] https://www.cyberciti.biz/faq/mv-command-howto-move-folder-in-linux-terminal/
