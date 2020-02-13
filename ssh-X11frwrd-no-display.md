# ssh user@host -X ja no DISPLAY

## Ongelma
Outo ongelma, kun yrittää etänä käynnistää graafisia (X Window System) ohjelmia 
esim: `xclock` tulostuu näytölle ilmoitus: ```Error: Can't open display```

## Ratkaisu

Muokkaa palvelimen ```/etc/ssh/sshd_config``` -tiedostoa, jotta siellä
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

Ensiksi otetaan normaali yhteys palvelimeen:

```
ssh kayttaja@palvelin -X
```

Käynnistetään esim. mooc.fi:n TMCbeans-ohjelma:

```
tmcbeans
```

luodaan siis ssh-yhteys ```palvelin``` -nimiseen tietokoneseen ```kayttaja``` -nimisellä käyttäjällä.

Yhteyden voi muodostaa myös ip-osoitteella esim: ```kayttaja@8.8.8.8 -X```

```-X``` tarkoittaa, että luodaan X Window System-tunneli, jolloin voi suojatun verkon yli suorittaa myös graafisia ohjelmia 

esim: ```firefox```, ```xclock```, ```chromium```, ```eclipse```, ```netbeans``` ja vaikka ```libreoffice``` ehkä jopa ```tuxrace```, mutta 3D-pelit saattaa toimia hitaasti/huonosti.

Graafisen ohjelman suorittamiseen tarvitaan myös asiakaskoneseen (mistå ssh-yhteys aloitetaan) X Window System. Graafisissa Unixeissa(mukaanlukien Mac OS X)/Linuxeissa on yleensä X. Mac OS X:ssä pitää asentaa jokin sisäänrakennettu lisäohjelma.

## Linkit
1. [comp.security.ssh: What does "X11UseLocalhost no" do?](https://groups.google.com/forum/#!topic/comp.security.ssh/ri8yJGOSfHQ)
1. [HY: Luento 6: X-tunnelointi ja tiedostonsiirto](http://www.ling.helsinki.fi/kit/2005s/clt130/luento6.shtml)
1. [Linux.fi: X Window System](https://www.linux.fi/wiki/X_Window_System)
1. [How do I run graphical programs remotely from a Linux server?](https://uisapp2.iu.edu/confluence-prd/pages/viewpage.action?pageId=280461906)
1. [X MS Windowsille - Cygwin/X](https://x.cygwin.com/)
1. [X MS Windowsille - Xming](http://www.straightrunning.com/XmingNotes/)
`
