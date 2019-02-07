# Vagrant - kätevä tapa ajaa virtuaalitietokoneita #

### Asennus ###

Vagrantin avulla on mahdollista hakea imaget kätevästi suoraan komennolla.

Ei tarvitse etsiä netistä .iso:a ja noudattaa monimutkaisia ohjeita<br>
esim. Mac Os X:n suorittamiseen.<br>
Vagrant tarvitsee VirtualBoxin toimiakseen.<br>
Se toimii myös esim. Hyper-V:llä,
mutta VirtualBoxille on julkaistu eniten imageja.

**VirtualBox**

Jostain syystä VirtualBoxin uusin versio ei toimi.<br>
Lataa ja asenna VirtualBox 5.2:<br>
(https://www.virtualbox.org/wiki/Download_Old_Builds_5_2)

Kun olet asentanut VirtualBoxin,<br>
pitää järjestelmä joissakin käyttöjärjestelmissä
käynnistää uudelleen.

**Extension Pack**

Kun VirtualBox on asennettu (ja joissakin tapauksissa järjestelmä käynnistetty uudelleen).<br>
Lataa ja asenna samalta sivulta Extension Pack:<br>
(https://www.virtualbox.org/wiki/Download_Old_Builds_5_2)

**Vagrant**

Lataa ja asenna Vagrant:<br>
(https://www.vagrantup.com/downloads.html)

----------------------------------------------------------------------

### Käyttö ###

Avaa terminaali(Linux ja Mac), tai komentokehoite (cmd, powershell)

Luo komentokehotteessa halumasi hakemisto esim:<br>
```
mkdir vagrant-linux
```
Siirry juuri tehtyyn hakemistoon:<br>
```
cd vagrant-linux
```

vagrant-linux hakemistossa ajetaan tämä komento:<br>
```
vagrant init ubuntu/xenial64
```

Ohjelma hake ubuntu-nimiseltä käyttäjältä xenial64-nimisen imagen,
eli 64-bittinen Ubuntu 16.04.

**Käynnistetään virtuaalikone**

Virtuaalikone käynnistetään up -komennolla:<br>
```
vagrant up
```

**ssh**

Virtuaaliseen komentopohjaiseen Linux/Unixiin pääsee ssh -komennolla:<br>
```
vagrant ssh
```

**Imagen tuhoaminen**

Jos halua aloittaa alusta ja tuhota kaikki virtualikonessa tekemät muutoksen:<br>
```
vagrant destroy
```


## Imaget <br>

Vagrant imageja voi selata tästä:<br>
(https://app.vagrantup.com/boxes/search)
-----------------------------------------------------------------------------

## Mac OS X - High Sierra ###

Tässä esimerkissä käynnistetään Mac Os X - High Sierra.
Tämä vaat, että Extension Pack on asennettuna.

**image** <br>
Löydettin imageista tämä:<br>
(https://app.vagrantup.com/burinkhazad/boxes/macos-high-sierra)

Loin vagrantMac -hakemiston:<br>
```
mkdir vagrantMac
cd vagrantMac
```

Initialisoin imagen:<br>
```
vagrant init burinkhazad/macos-high-sierra
```

Käynnistetään virtuaalikone:<br>
```
vagrant up
```

Tämä kestää kauan, sillä esim Linux/*BSD-imageissa imagen koko on muutamia megoja, kun taas Windows ja Mac-imaget saattaa olla muutamia gigoja.

**VirtualBox**

Avaa graafinen VirtualBox -ohjelma<br>
Valitse vagrantMac_default_154954...<br>
Ja paina Show.<br>
![VirtualBox show](https://github.com/lnxbusdrvr/docs/vagrant01.png)










