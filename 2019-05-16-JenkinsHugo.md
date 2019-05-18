
# Jenkins & Hugo -dokumentaatio

## Asenna nginx

```sudo apt install -y nginx```

Tarkista, että se on aktiivisena

```sudo systemctl status nginx```

Ja, että se käynnistyy järjestelmän alussa

```sudo systemctl enable nginx```

## Asenna hugo

```sudo apt install hugo```

## Jenkins paikallinen asennus

Asennetaan Jenkins paikallisesti testatakseen Hugoa ilman välikäsiä

### Asennetaan Java

```
sudo apt install openjdk-8-jdk
```

Kerrotaan järjestelmälle, missä javapolku on

### Editori 1: vi-editorilla muokkaaminen

Kirjoita terminaaliin

```
sudo vi /etc/environment
```

paina pikku ```o``` -kirjainta. o niin kuin olli molli, mutta pienellä o:lla.

*Tämä pikku o avaa uuden rivin kirjoitustilaan(edit/insert mode), tällöin joissakin vi-versioissa lukee* ```-- INSERT --```

kirjoitetaan, tai liitetään hiirellä seuraava rivi:

```
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/bin/"
```

Painetaan näppäimistöstä **ESC** -näppäintä

*ESC siirtää sinut komentotilaan*

kirjoitetaan tämä ```:wq```

Jossa:

- : Tämä kaksoispiste tarkoittaa komentorivitilaa (ehkä kutsutaan joskus eri nimellä)
- w Tämä pikku-w tarkoittaa, että tiedosto tallennetaan (write).
- q Tämä pikku-q tarkoittaa, että ohjelmassta poistutaan (quit).

*Huom! Jos meni pieleen, niin vi:stä voi poistua tallentamatta komennolla* **ESC-näppäin :q!**


### Editori 2: nano-editorilla muokkaaminen

Kommenna terminaalissa :

```sudo nano /etc/environment```

lisää tyhjälle riville tämä rivi:

```
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/bin/"
```

Paina näppäiminyhdistelmää: Ctrl+x (pikku x)

Ruudulle ilmestyy tämä:

> Save modified buffer?  (Answering "No" will DISCARD changes.)                   
 Y Yes
 N No

Paina **y**


ja **Enter**

### GUI Editori 3 ja 4: gedit ja -editorilla muokkaaminen

Komenna terminaalissa tämä

```sudo gedit /etc/environment```

tai

```sudo pluma /etc/environment```

Lisää tämä rivi tiedostoon:

```
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/bin/"
```

Ja tallenna hiirellä tiedosto 


## Muokkauksen jälkeen

Suorita tämä, joka ottaa käyttöön uudet asetukset


```
source /etc/environment
```

Tarkistetaan, että java-polku on voimassa

```
echo $JAVA_HOME
```

Pitäisi tulostua

> $ echo $JAVA_HOME
/usr/lib/jvm/java-8-openjdk-amd64/bin/

## Asennetaan Jenkins

Ensiksi kerrotaan repo-avain järjestelmälle

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

Lisätään repo debian apt.sources listaan

```
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/
jenkins.list'
```

Päivitetään apt listat

```
sudo apt update
```

Lopuksi asennetaan Jenkins

```
sudo apt install jenkins
```

## Avaa Jenkins

Avaa selaimessa osoite [localhost:8080](http://localhost:8080)


*BlueOceania ei tarvita, eli image voi olla myös tavallinen Jenkins*

- Kopioi ja liitä salasana ```sudo cat /var/lib/jenkins/secrets/initialAdminPassword```
- Asenna ehdotetut pluginit
- Luo haluamasi käyttäjätunnus
- Määritä Jenkins-url (oletus)
- Käynnistä Jenkins uudelleen, tarvittaessa aja tämä komento terminaalissa ```sudo systemctl restart jenkins.service```
- Selaimessa osoitteessa localhost:8080 Kirjaudu sisään


## Linkit

1. [Creating a CI/CD 'Draft' Website with Jenkins (and Hugo)](http://ryan.himmelwright.net/post/draft-website-with-jenkins/)
1. [how to setup ssh keys for jenkins to publish via ssh](how to setup ssh keys for jenkins to publish via ssh)
1. [Publish Over SSH Plugin](https://wiki.jenkins.io/display/JENKINS/Publish+Over+SSH+Plugin)
1. [ssh key generation using dockerfile](https://stackoverflow.com/questions/27504187/ssh-key-generation-using-dockerfile)
1. [](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04#installing-specific-versions-of-openjdk)
