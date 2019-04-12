
# Git kun teet haaroja

Kun teet omia haaroja(Branches), niin **älä poista** niitä masterista kopioituja tiedostoja uudessa haarassa **ikinä** (vaikka Erkki ja hänen koira sanoisi niin).

## Minä tein just niin

No niin, tietenkin.

1. Ota varmuuden vuoksi .zip-kopio haarastasi
1. Poista koneeltasi koko hakemisto
1. Ja aloita alusta

### Jatketaan

```
git clone git@github.com:username/repo.git
```

Kopioi poistamaasi tiedostot master-haarasta jonnekiin talteen

```
git checkout <sinun_haarasi>
git pull
```

Kopioi nämä juuri ```master``` -haarasta kopioimasi tiedostot sinne missä ne alunperin olikin

lisää kaikki nämä tiedostot git addilla uudelleen haaraan, committaa ja pushaa ne gittiin:

```
git add tiedosto_jossain.md jokuToinenTiedostoJossain.md README.md
git commit -m "Tiedostot palautettu"
git push -u origin <sinun_haarasi>
```

### Tämä ei ollut vielä ohi

Nyt siirry haaraan johoon haluat tehdä pull requestin.
Esim: 

master <--- sinun_haarasi

Siirry nyt sinun_haarasi:sta masteriin:

```
git checkout master
```

### Melkein ohi

Viimeiseksi pitää tehdä ```merge``` jotta tämä toimisi oikein

Olet siis master-haarassa ja komennat tämän:

```
git merge sinun_haarasi
```

Voilá nyt se on korjattu.

Saattaa olla, että jossakin välissä pitää tehdä myös ```git pull``` ohjelma kyllä ilmoittaa siitä sitten.

## Uuttaa tietoa

Tälläisissä tapauksissa vai omalle haaralle hakea mergen masterista, eikä tarvitse koko yö tapella ja siirrellä tiedostoja.

[Bring your feature branch up to date with master. ](https://gist.github.com/santisbon/a1a60db1fb8eecd1beeacd986ae5d3ca)

## git checkout <tiedosto>
  
```git checkout <tiedosto>``` palauttaa commitin siihen tilaan missä tämä tiedosto viimeksi oli.


Edit: 12.04.2019 klo 13:00
Еdit: 12.04.2019 klo 13:20
