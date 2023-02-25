# h10 DJ Ango 

Aloitin tehtävien tekemisen klo 22:15 25.2.2022

## a) kannattavaa 22:16

### kehitysympäristön pystytys ja djangon asennus 22:16

Aloitin lataamalla kehitysympäristön

    sudo apt-get -y install virtualenv

Kehitysympäristön lataamisen jälkeen tein uuden kehitysympäristön komennolla

    virtualenv --system-site-packages -p python3 env/

Ja siirryin juuri tekemääni kehitysympäristöön

    source env/bin/activate
    
Kehitysympäristön sisällä tein requirements.txt tiedoston komennolla

    micro requirements.txt

jonne kirjoitin django

![image](https://user-images.githubusercontent.com/112076377/221378149-641397df-7f18-4b10-b58a-d214ddc66c25.png)

ja latasin djangon vielä 

    pip install -r requirements.txt
    
### django 22:30

Tein uuden projektin djangoon komennolla

    django-admin startproject lassico
    
ja käynnistin vielä django sivuston komennoilla

    cd lassico
    
    ./manage.py runserver

![image](https://user-images.githubusercontent.com/112076377/221378622-6829f998-b01b-40c2-9cae-b75fab8ff2f1.png)

Käynnistäessä palvelinta django antaa varoituksen

![image](https://user-images.githubusercontent.com/112076377/221378832-70ac818b-cdae-414c-ad19-8aca318bb95c.png)

Poistin varoitukset tekemällä suositellut migraatiot komennoilla

    ./manage.py makemigrations
    ./manage.py migrate

Tein vielä uuden käyttäjän komennolla

    ./manage.py createsuperuser

Kirjauduin sisään palvelimelle kirjoittamalla käynnistyksen yhteydessä annetun ip-osoitteen perään /admin ja kirjauduin sisään juuri tehdyillä tunnuksilla

![image](https://user-images.githubusercontent.com/112076377/221378946-412f535e-9f5d-4486-8cb4-9107db9b7c43.png)








