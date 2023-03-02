# h11 prod

Aloitin tehtävien tekemisen 13:43 2.3.2023

## Palvelimen asennus ja testaus

Asensin apache2 palvelimen komennolla 

    sudo apt-get -y install apache2
    
Ja vaihdoin vielä apachen etusivun omalla etusivullani

    echo "The greater new frontpage" | sudo tee /var/www/html/index.html
    
Tein vielä static kansion pääkäyttäjäni kotihakemistoon
    
    mkdir -p publicwsgi/lassico/static/
    echo "The greater new static frontpage!"|tee publicwsgi/lassico/static/index.html

Lisäsin apacheen vielä uuden virtualhostin 

    sudoedit /etc/apache2/sites-available/lassico.conf
    
Ja lisäsin .conf tiedostoon 

![image](https://user-images.githubusercontent.com/112076377/222425224-29290e80-4f0e-4027-9240-2491ba1504de.png)

Lisäsin vielä uuden conf tiedoston käyttöön

    sudo a2ensite lassico.conf

Ja poistin vanhan conf tiedostoni

    sudo a2dissite newdefault.conf 

Ja kokeilin vielä koodin toimivuuden apachen configtestillä 

![image](https://user-images.githubusercontent.com/112076377/222425374-a97dc800-0d2e-4721-a2bd-5576a46ea795.png)

configtest ok joten käynnistin apachen palvelimen uudestaan, jotta muutokset näkyvät 

    sudo systemctl restart apache2
    
Ja uusi static kansio toimii 

![image](https://user-images.githubusercontent.com/112076377/222426604-66382684-eee8-473e-b101-95b1c5dc848c.png)

## Djangon lataus virtualenviin 14:19

Aloitin lataamalla virtualenvin komennolla

    sudo apt-get -y install virtualenv 
    
siirryin cd komennoilla aikaisemmin luomaani publicwsgi kansioon 

    cd 
    cd publicwsgi/
    
ja tein uuden virtualenvin publicwsgi kansiion komennolla 

    virtualenv -p python3 --system-site-packages env
    
Siirryin virtualenviin komennolla 

    source env/bin/activate
    
Loin uuden tiedoston microlla, jonka avulla lataan djangon

    micro requirements.txt
    
Jonka sisällä lukee django

![image](https://user-images.githubusercontent.com/112076377/222430430-6f290812-82bb-4d30-921a-b8f7d87950d4.png)

Ja latasin vielä djangon komennolla

    pip install -r requirements.txt

Varmistin vielä että djangon versio on vähintään 4

![image](https://user-images.githubusercontent.com/112076377/222431040-0d08f6c1-42a8-40d2-b919-ad0d27ba6b85.png)

## Djangon configurointi 14:52

Aloitin uuden projektin djangossa komennolla 

    django-admin startproject testico
    
Siirryin muokkaamaan aikasemmin tehtyä conf tiedostoa 

    sudoedit /etc/apache2/sites-available/lassico.conf

Käytin Tero Karvisen tekemää valmista pohjaa conf tiedoston tekemiseen, jossa tarvitsee vain vaihtaa pari polkua.

    Define TDIR /home/lassiv/publicwsgi/testico
    Define TWSGI /home/lassiv/publicwsgi/testico/testico/wsgi.py
    Define TUSER lassivar
    Define TVENV /home/lassiv/publicwsgi/env/lib/python3.9/site-packages
    # See https://terokarvinen.com/2022/deploy-django/

    <VirtualHost *:80>
            Alias /static/ ${TDIR}/static/
            <Directory ${TDIR}/static/>
                    Require all granted
            </Directory>

            WSGIDaemonProcess ${TUSER} user=${TUSER} group=${TUSER} threads=5 python-path="${TDIR}:${TVENV}"
            WSGIScriptAlias / ${TWSGI}
            <Directory ${TDIR}>
                 WSGIProcessGroup ${TUSER}
                 WSGIApplicationGroup %{GLOBAL}
                 WSGIScriptReloading On
                 <Files wsgi.py>
                    Require all granted
                 </Files>
            </Directory>

    </VirtualHost>

    Undefine TDIR
    Undefine TWSGI
    Undefine TUSER
    Undefine TVENV













