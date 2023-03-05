# h12 vianselvitys 5.3.2023 20:57

## Alkutilanne 20:59

Aloitin tehtävien tekemisen viimeisen kotiläksyn pohjalta, jossa pystytin toimivan djangon tuotantoasennuksen

Varmistin vielä, että kaikki toimii
![image](https://user-images.githubusercontent.com/112076377/222980407-49c62389-d3a6-44b6-beb4-6e12cdc9acd3.png)

![image](https://user-images.githubusercontent.com/112076377/222980524-644ba55b-a602-4bec-a235-c6834e14ea55.png)

## a) kirjoitusvirhe Python-tiedostossa

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
