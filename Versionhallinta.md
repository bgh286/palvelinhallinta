# Harjoitus 3 Versionhallinta
Tehtävä oli käyttää git komentoja sekä luoda uusi salt-moduli.

## Käytetyt alustat ja aloitus
Tehtävän tekemiseen käytin pöytäkonettani, jossa on asennettuna VirtualBox. Aloitin tehtävän käyttämällä harjoitus 1:ssä pystyttämääni Ubuntu 20.04 Desktop konetta, jossa on Salt Master sekä Minion asennettuna. Käytetyt alustat:
Windows 10, i7-6700, VirtualBox, Ubuntu 20.04 Desktop

Tunnilla käytiin git käyttöönottoa ja peruskomentoja (git pull, git push, git commit, git reset)

### Git log
Git log komento näyttää listan tehdyistä commiteista, joista uusin näkyy ensimmäisenä

![Git log](https://raw.githubusercontent.com/bgh286/palvelinhallinta/main/git_log.PNG)

### Git diff
Git diff komento vertailee kahta asiaa toisiinsa esim. kahta eri tiedostoa ja kertoo miten ne eroavat toisistaan

![Git diff](https://raw.githubusercontent.com/bgh286/palvelinhallinta/main/git_diff.PNG)

### Git blame
Git blame komento kertoo kuka ja milloin on tehty muutoksia millekin riville

![Git Blame](https://raw.githubusercontent.com/bgh286/palvelinhallinta/main/git_blame.PNG)

### Git reset --hard
Tein muutoksia Testikommitteja tiedostoon, jonka jälkeen käytin git reset --hard komentoa jolla palasin aiempaan versioon tiedostosta.

![Git reset](https://raw.githubusercontent.com/bgh286/palvelinhallinta/main/git_reset.PNG)

## Uusi Salt-moduli

Aloitin uuden Salt-modulin luomisen tuttuun tapaan testaamalla ensin hello world testillä. Testin onnistuttua siirryin asentamaan VLC-ohjelmaa Saltin kautta.

```
vlc_install:
  pkg.installed:
    - pkgs:
      - vlc
```

Kun sain asennettua VLC:n Saltin kautta, siirryin muokkaamaan konfiguraatio tiedostoa, joka sijaitsee /home/KÄYTTÄJÄ/.config/vlc/vlcrc.
Lisäsin .sls tiedostoon alla olevan pätkän.
```
/home/robin/.config/vlc/vlcrc:
  file.managed:
    - source: salt://vlc/vlcrc
```
Muokkasin vlcrc konfiguraatio tiedostoa alla olevalla tavalla sekä ajoin alla näkyvän komennon.
```
sudo salt '*' state.apply vlc
```
![VLC config](https://raw.githubusercontent.com/bgh286/palvelinhallinta/main/vlc_custom.PNG)
