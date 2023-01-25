# Koodien lisenssit

Aloitin tehtävien teon 10:28 25.1.2023 

## FSF lisenssi

FSF free software definition eli FSF lisenssi on yksi suosituimmista vapaista lisensseistä.
FSF pitää sisällään 
- Vapaus pyörittää ohjelmistoa kuin haluaa, mihin tahansa tarkoitukseen.
- Vapaus opiskella miten ohjelmisto toimii sekä muuttaa sitä. 
- Vapaus levittää kopioita ohjelmistosta.
- Sekä vapaus levittää muokattua ohjelmistoa.

   https://www.gnu.org/philosophy/free-sw.html

## Open source lisenssien kasvu

Mikko Välimäki esittelee kirjassaan The Rise of Open Source Licensing väitteitä sekä puolesta että vastaan avoimen lähdekoodin lisseistä
- Vapaan lähdekoodin ohjelmistot innostavat kehittäjiä muokkaamaan alkuperäistä koodia uusiin tarkoituksiin sekä parantelemaan sitä 
- Suuret yritykset rajoittavat ohjelmistojaan tiukemmilla lisensseillä, jotka estävät lähdekoodin näkemisen
- Tiukat lisenssit motivoi isoja yrityksiä, koska muut eivät voi kopioida niitä yhtä helposti
- Löysemmät lisenssit luo tilaa kehitykselle

   http://lib.tkk.fi/Diss/2005/isbn9529187793/isbn9529187793.pdf

## Kolmen ohjelman lisenssit

Fortune
- MIT-lisenssi
- Ohjelman github repositoriossa näkyy ohjelman lisenssi
- MIT lisenssi on vapaa lisenssi 
- MIT lisenssi sallii kehittäjien muokata, kopioida, käyttää ja levittää ohjelmistoa tai sen muokattua versiota. MIT lisenssi tulee olla myös jatkokehitetyissä ohjelmissa
- https://github.com/shlomif/fortune-mod/blob/master/LICENSE

cmatrix
- GNU-lisenssi
- Ohjelman github repositoriossa näkyy ohjelman lisenssi
- GNU lisenssi on vapaa lisenssi 
- GNU-lisenssi antaa muille kehittäjille oikeuden kopioida, levittää sekä muokata sitä. GNU lisenssi tulee olla myös jatkokehitetyissä ohjelmissa
- https://github.com/abishekvashok/cmatrix/blob/master/COPYING

figlet 
- BSD-lisenssi
- Ohjelman github repositoriossa näkyy ohjelman lisenssi
- BSD-lisenssi on vapaa lisenssi 
- BSD-lisenssi antaa muille käyttäjille samat oikeudet kuin kaksi ylempää vapaata lisenssiä rajaten patentoinnin. 
- https://github.com/cmatsuoka/figlet/blob/master/LICENSE

## Grep lausekkeet

Grep lauseke regex

    Grep -P '[mM]onkey' monkey

[mM] regex tarkoittaa lausekkeessa että tekstitiedostosta "monkey" haetaan sekä isoilla että pienillä alkukirjaimilla

![image](https://user-images.githubusercontent.com/112076377/214582399-1853ffab-4b81-46c0-9e45-53826ba4e8cf.png)

Grep lauseke putkilla 

    Grep -P '[mM]onkey' monkey | wc -l
    
Sama lauseke putkella wc -l laskee grep lausekkeen printtaamat rivit. Rivejä jossa on isolla tai pienellä "monkey" on yhteensä 4 kappaletta

![image](https://user-images.githubusercontent.com/112076377/214583697-d73a319f-f75b-4eea-a824-4c9250736bcf.png)

## Loppusanat

Sain tehtävät valmiiksi 16:05
