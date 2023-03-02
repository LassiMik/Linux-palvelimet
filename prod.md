# h11 prod

Aloitin tehtävien tekemisen 13:43 2.3.2023

## Palvelimen asennus ja testaus

Asensin apache2 palvelimen komennolla 

    sudo apt-get -y install apache2
    
Ja vaihdoin vielä apachen etusivun omalla etusivullani

    echo "The greater new frontpage" | sudo tee /var/www/html/index.html
    
Tein vielä static kansion pääkäyttäjäni kotihakemistoon
    
    mkdir -p publicwsgi/lassico/static/
    echo "The greater new static frontpage!"|tee publicwsgi/lassico/static/index.html
