## CentOs 7 ja UEFI

Normaalisti kun asentaa CentOs 7, niin järjestelmä ei osaa luoda uefi-juttuja<br>
Tässä ohjeessa on fixi, miten uefin saa asennettua.<br>

Installation source kohdasta valitsin **http://** <br>
ja lisäsin siihen osoitteen: **mirror.centos.org/centos/7/os/x86_64/** <br>

Minulla on 536M osio /dev/sda1, jolla on **boot** ja **eps** -flagit

Kun CentOsin asennusohjelma on asentanut kaikki paketit ja se odottaa,
että käyttäjä painaa reboot-nappia. Ennen sitä tein nämä asiat,
näitä ei valttämättä kaikkia tarvitse tehdä, mutta näin tein.

## Siirrytään shelliin

Siirrytään shelliin painamalla tätä näppäinyhdistelmää:

```
<ctrl>+<alt>+<F2>
```

Esiin tulee shelli

## efivarfs-modulen lataus

Latasin efivarfs-modulen:

```
modprobe efivarfs
```

## chroot

Sen jälkeen chroottasin /mnt/sysimage -hakemistoon,
jolloin tästä hakemistosta tuli uusi juurihakemisto:

```
chroot /mnt/sysimage
```

## efivarfs
Latasinn taas kernel modulen, mutta nyt chrootin sisällä

```
modprobe efivarfs
```

## Asennetaan efivar -paketti

```
yum install efivar
```


## Asennetaan grub2-efi-x64-modules.noarch -paketti

```
yum install grub2-efi-x64-modules.noarch
```

## Tarkistetaan grub-kirjastoja

```
ls /usr/lib/grub
```

Tässä pitäisi näkyä ```x86_64-efi``` -hakemisto

## Initialisoidaan grub2 ensimmäiselle kovalevylle

```
grub2-install /dev/sda
```

Valmis

Ihmettelen kyllä, että miksi tämä ei toiminut ajemmin, mielestäni kyllä yritin tätä samaa tapaa,
mutta **/usr/lib/grub** -hakemistossa oli silti vain i386-pc -hakemisto
