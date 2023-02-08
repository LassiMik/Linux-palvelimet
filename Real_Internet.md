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

- Palomuurin tekemisen jälkeen uuden käyttäjän luonti

      sudo adduser lassi
      
- Sekä oikeuksien antaminen 
           
      sudo adduser lassi sudo
      sudo adduser lassi adm
      sudo adduser lassi admin

- Root käyttäjän lukitseminen uuden käyttäjän luonnin jälkeen

      sudo usermod --lock root
      
- Sekä root kijautumisen estäminen SSH komennolla

      sudoedit /etc/ssh/sshd_config
          # ...
          PermitRootLogin no
          # ...
      sudo service ssh restart

- Seuraavaksi tulee päivittää kaikki koneen tiedostot helpolla komennolla

      sudo apt-get update
      sudo apt-get upgrade
      
- Toisen reiän tekeminen ufw palomuuriin, jotta käyttäjät pääsevät nettisivulle

      sudo ufw allow 80/tcp

- Apachella voi käyttää IP-osoitetta sivulle pääsemiseen, mutta vuokraamalla DNS nimen saat paljon käyttäjäystävällisemmän osoitteen sivustollesi kuten vartiainen.me
- Palvelimen nimen toimivuutta voi kokeilla komennolla. Kokeile selaimella toimivuutta vasta, kun nimi oikeasti toimii. Muuten vanha ja väärä nimi tallentuu selaimesi paikalliseen nimipalvelimeen

      host example.com dns1.registrar-servers.com
      
## a) oma virtuaalipalvelin 15:21




















## Lähteet

[1] https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
