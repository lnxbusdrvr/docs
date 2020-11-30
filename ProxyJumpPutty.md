# RDP porttiohjaus Puttylla Windowsissa

## Putty:ssa

## Session

Session-välilehti:

`Host Name(or IP adress)`: <Sen_konen.ip-osoite_jonka_kautta_mennään_sisäverkkoon>

Eli tyyliin: `Host Name(or IP adress): 123.456.78.9` tai `Host Name(or IP adress): joku.kone.fi`

`Saved Sessions`: <tänne_joku_nimi_Vaikka_kone2rdpVia.joku.kone.fi_lopussa_tämä_konfiguraatio_tallennetaan_tänne>

Eli `Saved Sessions`: kone2rdpVia.joku.kone.fi

## SSH

### Tunnels

SSH --> Tunnels-välilehti:

Port forwarding:

`|x| Local ports accept connections from other hosts`

Add new forwarded port:

`Source port`: 9627

`Destination`: <sisäverkon_sisällä_olevan_konen_osoite>:3389

Eli tyyliin `10.0.0.1:3389`, tai `jokukone2.kone.fi:3389`

Paina `Add`

## Tallenna asetukset

### Sessions

Sessions-välilehti:

Paina save, niin `kone2rdpVia.joku.kone.fi` -niminen asetus tallentuu

## Avataan yhteys

Sessions-välilehti:

Valitaan äsken tallennettu asetus ja painetaan `Open`

Putty kysyy käyttäjätunnusta ja salasanaa

Salli Windowsin palomuuriasetukset

Nyt porttiohjaus on luotu



## käynnistetään Windowsin Remode Desktop

paina näppäimistöstä `<win>+r` ja kirjoita `mstsc`, joka avaa remote desktop-sovelluksen
kirjoita osoitteeksi: `localhost:9627`




### Onko portti lisätty?

Seuraavalla komenolla voi nähdä auki olevat portit

```
netstat -an
```

## Linkit
1. [Native SSH Port Forwarding (Tunneling) on Windows 10](http://woshub.com/ssh-tunnel-port-forward-windows/)
2. [Portforwarding with SSH (Putty)](https://www.akadia.com/services/ssh_putty.html)
