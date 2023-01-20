# Virtuaalitietokoneen lataus ja Debianin asennus siihen
 Käyttöjärjestelmä: 
 WIN 10 Home
 
 Ram: 
 32 GB
 
 Fyysistä muistia: 
 500GB
 
 Virtuaaliohjelmistona toimii Oraclen VM VirtualBox Manager
 
 Debianin Iso tiedosto: debian-live-11.6.0-amd64-xfce+nonfree.iso.
 
 Aloitin latauksen 20.1.2023 klo 15:32
 
## Aloitus
 
 Aloitin lataamalla Oraclen VM VirtualBox Managerin Oraclen  nettisivulta https://www.virtualbox.org. Seuraavaksi myös asensin Debian ISO tiedoston hakemalla netistä "debian non-free live iso". Tarvitsemme ISO tiedostoa myöhemmin tehdessämme virtuaalikonetta.
 
 Kun VirtualBox on ladattu ja käynnistettu uuden virtuaalikoneen saa tehtyä painamalla vasemmalla ylävalikossa "machine" ja alasvetovalikosta "new", joka vie virtuaalikoneen luontinäkymään. "name" kohtaan voi laittaa minkä haluaa virtuaalikoneensa nimeksi. Folder ainakin itsellä meni suoraan oikeaksi eli pidä se oletussijaintina. Iso imageen laitetaan juuri lataamamme Debian ISO tiedoston tiedostosijainti. Typeen tulee Linux ja versioon Debian 64-bit. Memoryyn ja prosessorien määrään voi laittaa mitä vain mutta suosittelen ainakin 4 gigaa ramia. Prosessorejakin voi laittaa monta mutta suosittelen käyttämään vain yhtä.
 
 Lopuksi paina "Finish" valikon oikeasta alareunasta
 
 Nyt sinulla on oma virtuaalinen linux tietokone!
 
 Virtuaalitietokoneen voi käynnistää tuplaklikkaamalla VirtualBox managerissa uutta virtuaalitietokoneesi pikakuvaketta. Koneen käynnistyessä tulee vastaan startup valikko jossa valitaan ylin vaihtoehto eli Debian GNU/Linux Live (kernel versio-amd64). Valikossa voi liikkua nuolinäppäimillä sekä valita valinnan entteriä painamalla.
 Kun olet päässyt virtuaalitietokoneesi työpöydälle kannattaa käydä kokeilemassa toimiihan selain oikein valitsemalla virtuaalikoneen vasemmasta yläreunasta "Applications" ja "Web Browser". Jos selain toimii normaalisti Päästään seuraavan työvaiheeseen.
 
 Palataan työpöydälle sulkemalla selain ja valitaan työpöydältä pikakuvake nimeltä "install debian" joka aloittaa debianin asennuksen virtuaalikoneelle. Ensiksi asennusohjelmasta valitsemme sijainnin (Helsinki) sijaintia voi vaihtaa joko painamalla kartasta Suomea tai etsimällä hakemistosta. Seuraavassa vaiheessa valitsemme näppäimistön kieleksi suomen vasemmasta hakemistosta (Finnish) sekä oikean puoleisesta hakemistosta Finnish(classic, no dead keys). Näppäimistöä voi vielä kokeilla valintojen alla olevaan kenttään. Seuraavana kohtana on "Partitions" josta valitaan "Erase disk" ja alhaalla olevasta "boot loader location" valitaan "Master Boot Record". Seuraavaksi "Users" kohdassa laitetaan oma oikea nimi, käyttäjän nimi (käytetään kun kirjaudutaan virtuaalikoneeseen), tietokoneen nimi (kannattaa olla anonyymi) sekä salasana. Tarkastetaan vielä yhteenveto ja painetaan install.
 
 Debianin asentamisen jälkeen käynnistä virtuaalikone uudestaan.
 
 ## Komentokehote

