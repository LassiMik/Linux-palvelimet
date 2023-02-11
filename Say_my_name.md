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





## Lähteet

[1] https://docs.github.com/en/enterprise-server@3.4/pages/getting-started-with-github-pages/unpublishing-a-github-pages-site
