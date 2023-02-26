# h10 DJ Ango 

Aloitin tehtävien tekemisen klo 22:15 25.2.2023

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

## Tietokannan luonti 26.2.2023 klo x

Loin uuden django appin komennolla

    ./manage.py startapp blacklist
    
Ja lisäsin juuri tehdyn appin settings.py tiedostoon

    micro lassico/settings.py
    
![image](https://user-images.githubusercontent.com/112076377/221409154-79e92ad9-ffbb-4d32-bb8b-12a36c57e1e9.png)

Muokkaan juuri lisättyyn tietokantaan uuden taulun 
    
    micro blacklist/settings.py
    
![image](https://user-images.githubusercontent.com/112076377/221409393-29f55c38-0e1f-4e7b-a3c7-455bacd3dafc.png)


## Tietokannan luonti 22:54 

Loin tietokannan komennolla

    ./manage.py startapp crm
    
ja lisäsin crm settings.py tiedostoon 

    micro lassico/settings.py

![image](https://user-images.githubusercontent.com/112076377/221379270-181dcefb-ff71-4525-843f-2cffa27b3b22.png)

Muokkaan juuri lisätyn crm kansion sisällä olevaan models.py uuden tietokanta taulun

    micro crm/models.py
    
![image](https://user-images.githubusercontent.com/112076377/221379406-b848bc3e-45e9-4242-b597-40adce1648aa.png)

Ja vielä tuttuun tapaan migraatiot

![image](https://user-images.githubusercontent.com/112076377/221379477-b31acc41-35ef-433b-b8c3-65c181db0f90.png)

Rekisteröin vielä uuden tietokannan komennolla

    micro crm/admin.py
    
![image](https://user-images.githubusercontent.com/112076377/221379524-bbd425d7-6e50-4b33-bd5c-8a096052f0c4.png)




