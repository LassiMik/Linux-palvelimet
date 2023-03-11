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




Jatkan tästä huomenna
