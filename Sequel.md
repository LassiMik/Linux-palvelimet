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




    
