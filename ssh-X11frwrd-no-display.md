# ssh user@host -X ja no DISPLAY

## Ongelma

Eli, kun yrittää etänä ajaa graafisia (X Window System) ohjelmia i
esim: `xclock` tulstuu näytölle ilmoitus: ```Error: Can't open display```

## Ratkaisu

Muokkaa, palvelimen ```/etc/ssh/sshd_config``` -tiedostoa, jotta siellä
olisi nämä kohdat:

/etc/ssh/sshd_config:

```
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost no
```

Varsingkin kohta: ```X11UseLocalhost no``` tuntui olevan ratkaiseva muutos toimivuuteen.

### ssh x11 forwarding kertaus

Graafisia ohjelmia suojatun X-tunnelin läpi voi siis ajaa näin:

Ensiks otetaan normaali yhteys palvelimeen:

```
ssh kayttaja@palvelin -X
```

Käynnistetään mooc.fi:n TMCbeans-ohjelma:

```
tmcbeans
```

luodaan siis ssh-yhteys dd```palvelin``` -nimiseen tietokoneseen ```kayttaja``` -nimisellä käyttäjällä`.

Yhteyden voi muodostaa myös ip-osoitteella esim: ```kayttaja@8.8.8.8 -X```

```-X``` tarkoittaa, että yhteydessä käytetään myös X-palvelinta.
Tällöin myös asiakaskoneessa (mistå ssh-yhteys aloitetaan) on oltava X-ikkunointijärjestelmä. Graafisissa Unix(mukaanlukien Mac OS X)/Linuxeissa on yleensä X.

## Linkit
1. [comp.security.ssh: What does "X11UseLocalhost no" do?](https://groups.google.com/forum/#!topic/comp.security.ssh/ri8yJGOSfHQ)
1. [HY: Luento 6: X-tunnelointi ja tiedostonsiirto](http://www.ling.helsinki.fi/kit/2005s/clt130/luento6.shtml)
1. [Linux.fi: X Window System](https://www.linux.fi/wiki/X_Window_System)
`
