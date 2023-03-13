# h14 Uusi komento

Aloitin tehtävien teon 11.3.2023 klo 23:25

## Tee Linuxiin uusi komento Bashilla 23:26

Aloitin tekemällä uuden kansion komentoja varten kotihakemistoon selvemmän tiedostorakenteen takia.

    mkdir scripting
    
Tein helpon bash scriptin joka yhdistää kolme valmista scriptiä yhdeksi helposti muistettavaksi komennoksi

![image](https://user-images.githubusercontent.com/112076377/224512542-5b6999f3-1ff7-4b48-96b1-59022452b4ea.png)

Muutin myös uuden komennon oikeuksia, jotta kaikki käyttäjät voivat käyttää komentoa

    chmod ugo+x where

![image](https://user-images.githubusercontent.com/112076377/224512436-b2a4944f-5588-4d70-bb30-c18182f6bc4c.png)

Kopioin seuraavaksi valmiin scriptin kansioon, josta jokainen käyttäjä voi pyörittää sitä 

    sudo cp where /usr/local/bin/

![image](https://user-images.githubusercontent.com/112076377/224514049-0bab839b-fec7-4103-bfff-7b42041f3e18.png)

Kokeilin vielä scriptiä vaihtamalla käyttäjää 

    su lassivar
    
![image](https://user-images.githubusercontent.com/112076377/224514098-75575d84-d4df-4e49-8b80-02a32df087f7.png)

## b) Linuxiin uusi komento Pythonilla 13.3.2023 klo 14:27

Päätin kokeilla tehdä pythonilla komennon joka luo hakemiston ja nimeää sen käyttäjän syöttämällä nimellä

tein micro editorilla python tiedoston, johon kirjoitin 

![image](https://user-images.githubusercontent.com/112076377/224702009-a3a34c0d-7da5-41b9-90de-d76b5b14d0c9.png)

Seuraavaksi annoin kaikille käyttäjille oikeuden käyttää komentoa 

    chmod ugo+x folders.py

Muutin vielä komennon tiedostonimeä, jotta se on helpompi kirjoittaa

    mv folders.py folders

Kopioin vielä valmiin scriptin kansioon, josta jokainen käyttäjä voi käyttää sitä

    sudo cp where /usr/local/bin/

![image](https://user-images.githubusercontent.com/112076377/224703270-1c3116ba-370c-43a7-beb2-3092c4401af3.png)





Jatkan tästä huomenna
