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

Valitsin DigitalOceanin virtuaalipalvelin tarjoajakseni, koska sain github educationin avulla ilmaisen palvelimen vuodeksi.
Hyödyntääkseni github educationia jouduin tekemään uuden github käyttäjän, jossa on kouluni sähköpostiosoite.

Käyttäjän tekemisessä sivulle ilmeni ongelmia, kun jouduin odottamaan vahvistussähköpostia tunnin. Saatuani sähköpostin siirryin luomaan ensimmäistä projektia.
Projektin tehtyäni tein uuden dropletin, joka tarkoittaa uuden virtuaalipalvelimen luontia. Valitsin palvelimekseni halvimman mahdollisen, jossa on vähintään 1GB ramia.

Valitsin vielä käyttöjärjestelmäkseni Debian 11. 

![image](https://user-images.githubusercontent.com/112076377/217543960-da1a9c78-2db8-4622-8fc6-aa9c165cb76b.png)


## b) alkutoimet omalla virtuaalipalvelimella 15:31

Kirjauduin juuri luomalleni virtuaalipalvelimelle komennolla

      ssh root@palvelimen IP-osoite

Ja syötin salasanan, jolla kirjaudun DigitalOceaniin. Kun pääsin kirjauduttua ensitöikseni latasin ufw palomuurin komennolla

      sudo apt-get install ufw
      
Ja muutin ufw asetusta etten lukitse itseäni ulos palvelimelta

      sudo ufw allow 22/tcp

ja palomuurin laitto päälle

      sudo ufw enable

Seuraavaksi päivitin kaikki palvelimen tiedostot komennolla 
      
      sudo apt-get update
      sudo apt-get upgrade
      
Alkutoimien jälkeen tein vielä käyttäjän itselleni, jotta en joutuisi käyttämään roottia kokoajan komennoilla

      sudo adduser lassiv
      sudo adduser lassiv sudo
      sudo adduser lassiv adm

Roottiin kirjautumisen salasanalla esto 

      sudo usermod --lock root
      
Sekä vielä SSH kirjautumisen roottiin estäminen

      sudoedit /etc/ssh/sshd_config
      
Jossa vaihdoin seuraavan kohdan:

![image](https://user-images.githubusercontent.com/112076377/217545295-d6091f03-4108-4bf0-a96e-3d7d35b6868b.png)

      sudo service ssh restart

Nyt kun virtuaalipalvelimeni on kunnossa siirryn lataamaan apachea ja perustamaan web palvelinta

## Web palvelin omalle virtuaalipalvelimelleni

Aloitin lataamalla apachen komennolla

      sudo apt-get install apache2
      
Apachen latauksen jälkeen muutin apachen testietusivun komennolla

      echo moi | sudo tee /var/www/html/index.html

Muutin vielä yhtä ufw asetusta niin että sivustolleni pääsee

      sudo ufw allow 80/tcp

## d) merkkejä murtautumisyrityksistä 15:52









## Lähteet

[1] https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
