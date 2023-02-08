# h6 Real Internet

Aloitin tehtävien teon klo 14:49 8.2

## x) lue ja tiivistä 14:49

[1] Luin Tero Karvisen vuonna 2012 kirjoittaman artikkelin: *First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS* Ja tiivistin sen pariin ranskalaiseen viivaan

- Karvinen suosittelee käyttämään aina hyvää salasanaa, koska murtautumisyritykset ovat yleisiä
- Yksityinen virtuaalinen palvelin kannattaa perustaa lähelle tulevia asiakkaita. Jos tiedät, että suurin liikenne sivullesi tulee Euroopasta, kannattaa palvelin perustaa eurooppaan.
- Virtuaalisen palvelimen perustamisen jälkeen voit kirjautua palvelimellesi komennolla, jossa *ip-osoite* on virtuaalisen palvelimesi ip-osoite

      ssh root@ip-osoite

- Heti virtuaalipalvelimelle kirjautumisen jälkeen kannattaa ladata ufw palomuuri sekä asettaa pari asetusta oikein, ettet lukitse itseäsi ulos omalta palvelimeltasi

      sudo ufw allow 22/tcp
      
      
      sudo ufw enable
