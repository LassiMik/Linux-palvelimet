# h9 Sequel
Aloitin tehtävien teon 13:53 15.2

## x) yrityssoftaa 13:53

Youtube on esimerkki palvelusta, jossa koodi ajetaan palvelimella ja taustalla hyrrää tietokanta. Taustalla olevan tietokannan avulla youtube voi tallentaa
käyttäjien videoita samanaikaisesti lukitsematta ketään ulos sekä antaa monien käyttäjien kommentoida videoita. 

Vaihtoehtoisia toteutustapoja on tiedon kovatallentaminen kiintolevyille, josta tarvittaessa palvelin hakee tiedon. Tämä toteutustapa on huono, koska se on hidasta ja 
monet eivät voi samanaikaisesti tallentaa samalle kiintolevylle tai tiedostot voivat vahingoittua.

## a) Postgre 14:02

Asensin postgresql komennolla

    sudo apt-get update
    
    sudo apt-get install postgresql
    
jonka jälkeen käynnistin postgresql komennolla

    sudo systemctl start postgresql
    
Tein vielä toiselle käyttäjälleni, jolle en tunnilla tehnyt tietokantaa ja käyttäjää komennoilla

    sudo -u postgres createdb lassivar
    
    sudo -u postgres createuser lassivar
    
Vaihdoin käyttäjälle, jolle tein tietokannan ja käyttäjän komennolla 

    su lassivar
    
Testasin vielä tietokannan toimivuutta helpolla select lausekkeella

![image](https://user-images.githubusercontent.com/112076377/219023995-577578aa-bb2b-448c-ac00-aa03a0ab0593.png)

## b) CRUD 14:15

Aloitin CRUDin C kohdasta eli Create 

![image](https://user-images.githubusercontent.com/112076377/219025077-95bcffed-8f51-47e3-94b9-ea49b23cba50.png)

Seuraavaksi täytin tietokantaan vähän tietoa, jota voin testata 

![image](https://user-images.githubusercontent.com/112076377/219025833-7a76ebcb-4865-4c57-b460-0a59472eea8c.png)

Siirryin CRUDin R kohtaan eli read. 

![image](https://user-images.githubusercontent.com/112076377/219026130-7d6c48bf-87b5-4ec7-8ece-9defd5d26b2b.png)



    
