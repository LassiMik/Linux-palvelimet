# h8 Say my name

Alotin tehtävien teon 15:45 11.2

## a) Domainnimen vuokraus 15:45

Valitsin domainnimen vuokraukseen Namecheap nimisen palvelun, koska saan vuodeksi ilmaisen domainnimen github-education edulla.

Tein oman tilin namecheap sivustolle ja yhdistin oman github-education tilini siihen. Namecheap rajaa github educationin tarjoaman ilmaisen vuoden domainnimen koskemaan vain
.me ylätason verkkotunnuksia. Valitsin domainnimekseni lassivartiainen.me, koska se oli vapaana. Kun käytin github tiliäni saadakseni alennuksen github loi automaattisesti github pages repositorion käyttäjälleni.

Vuokrattuani oman domainnimeni siirryin Advanced DNS kohtaan, jossa voin vaihtaa DNS nimen osoittamaan omaan aikaisemmin tehtyyn palvelimeen. Kun kokeilin vaihtaa mitä 
sivustoni näyttää, kun kirjoitan osoitteen DNS nimenä vastaan tulee vain github pages tiedosto, jonka github automaattisesti loi. Vaihdoin github tilille, jonne pages repositorio luotiin ja kävin noudatin githubin ohjeita miten pages tiedosto otetaan alas [1]

![image](https://user-images.githubusercontent.com/112076377/218263329-f405e106-5bbe-4271-b66a-e25ec06783a4.png)


Tältä näytti valmiit advancedDNS asetukset. Lisäsin itse vain kaksi kohtaa ja loput namecheap oli luonut valmiiksi. Lisäsin vain nämä kaksi: 

![image](https://user-images.githubusercontent.com/112076377/218263364-4b5656f0-2291-4c9a-a31b-a66ae942b622.png)

 Kun olin poistanut github pages -linkin nettisivullani kesti noin 40 minuuttia, jonka jälkeen DNS nimi alkoi osoittamaan omalle palvelimelleni

![image](https://user-images.githubusercontent.com/112076377/218263473-20a59f64-87d1-465d-8104-cd36aec22ea4.png)

Sivustoni toimii!

## b) Oman DNS nimen tutkiminen 16:38

Aloitin tutkimisen host komennolla.

    host lassivartiainen.me

![image](https://user-images.githubusercontent.com/112076377/218264171-8299a52c-401c-4379-9969-160beff74d32.png)

Host komento tulostaa monta eri IP-osoitetta, jotka namecheap loi valmiiksi sekä oman palvelimeni IP-osoitteen, jonka laitoin ylemmässä kohdassa. IP-osotteiden lisäksi host tulostaa eforward1-5.registrar-servers.com, jotka ovat namecheapin omia osoitteita.

Seuraavaksi tarkastelen omaa palvelintani dig komennolla [2]
Lataan dig komennon 

    sudo apt-get install dnsutils
    
Jonka jälkeen tarkastelin palvelintani komennolla

    dig 164.90.178.115 lassivartiainen.me
    
Dig komennon jälkeinen osoite on palvelimeni IP-osoite, jonka jälkeen tulee palvelimeni DNS osoite.

![image](https://user-images.githubusercontent.com/112076377/218265723-22c23811-5e39-4e43-a938-cb0822d40c83.png)

![image](https://user-images.githubusercontent.com/112076377/218265709-197027fa-fe0a-4767-8064-a2222ce08ccb.png)

En osaa tulkita dig komennosta muuta, kuin palvelimen osoitteen ja palvelimen vastausajan, joka oli 180ms DNS osoitteessa ja 16ms IP-osoitteessa

Tehtävät sain valmiiksi 17:06

## Lähteet 17:07

[1] https://docs.github.com/en/enterprise-server@3.4/pages/getting-started-with-github-pages/unpublishing-a-github-pages-site

[2] https://phoenixnap.com/kb/linux-dig-command-examples
