# Jenkins SSH-avain GitHub deploy

## Asennetaan Publish Over SSH Plugin

Jenkinsissa

Manage Jenkins -> Manage Plugins -> Available -> Artifact Uploaders -> **Publish Over SSH**

**Download now and install after restart**

[x] Restart Jenkins when installation is complete and no jobs are running

*Jenkins ehkä ilmoittaa, että jotain meni pieleen, mutta näköjään se sitten kuitenkin toimii ihan hyvin.*

Pääsivulle pääset taas menemällä osoitteseen (localhost:8080)


## Luodaan ssh-avain

Mene linuxin terminaaliin

kirjaudu sisään jenkins-käyttäjänä:

```sudo su jenkins```

Siirry jenkins-käyttäjän kotikansioon:

```
cd
```

Olet tässä hakemistossa:

```
pwd
```

Luo ssh-avain:

```
ssh-keygen
```

Avaimet ovat 

```/var/lib/jenkins/.ssh/id_rsa```` ja ```/var/lib/jenkins/.ssh/id_rsa.pub```

## Jenkins selaimessa

Manage Jenkins -> Configure Jenkins -> Publish over SSH -> Jenkins SSH Key -> Key

kopioi tänne privatti ssh avain ```cat /var/lib/jenkins/.ssh/id_rsa```

**Apply**

**Save**


### Kerrotaan GitHub deploy-avain

Mene omalle [repo-sivulle](https://github.com/lnxbusdrvr/mdfilesforhugo)

Valitse seuraavasti

Settings -> Deploy keys -> **Add deploy key**

	Title:
		Hugo Jenkins
	Key
		tänne sisältö tiedostosta /var/lib/jenkins/.ssh/id_rsa.pub
	[x] Allow write Access
**Add key**

*Sisällön tiedostosta saa Linuxissa tällä komennolla* 
```cat /var/lib/jenkins/.ssh/id_rsa.pub```






