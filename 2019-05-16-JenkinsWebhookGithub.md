# Jenkins ja GitHub Webhook

## Asennetaan Jenkinsissa Github Integration plugin

Jenkinsissa

Manage Jenkins -> Manage Plugins -> Available -> 

 	Build Triggers
		Build Wrappers
			[x] GitHub Integration

**Download and install after restart**

[x] Restart ...

Käynnistä Jenkins uudelleen (http://localhost:8080/)

## Luodaan Jenkins projekti

Jenkinsissa:

New Item -> Syötä Projektin nimi -> Freestyle Project -> OK

	General
		Description
			Rakenna ja generoi www-sivu
		[x] GitHub Project
			Project url:
				git@github.com:github_kayttajatunnus/repo.git
		Source Code Management
			(o) Git
				Repositories
					Repository URL:
						git@github.com:github_kayttajatunnus/repo.git
					Credentials
						Add
							Jenkins

### Jenkins Credentials Provider: Jenkins -sivulla

	Add Credentials
		Domain:
			Global credentials (unrestricted)
		Kind:
			SSH Username with private key
		Scope:
			Global (Jenkins, nodes, items, all child items, etc)
		Username:
			GitHub_kayttajatunnus
		Private key
			(o) Enter directly
				liitä tänne sisältö tiedostosta: /var/lib/jenkins/.ssh/id_rsa.pub

*Sisällön saa näkviin Linuxin terminaalissa tällä komenolla* ```cat /var/lib/jenkins/.ssh/id_rsa.pub```

Valitse lopuksi **Add**


### Takaisin General ja Build Triggers välilehdellä

	Build Triggers
		[x] GitHub hook trigger for GITScm polling
	
	Build
		Add build step
			Execute shell
				Command
					hugo -D -F -b "http://localhost" -d public
		Add build step
			Execute shell
				Command
					rsync -r "$WORKSPACE/public/" /var/www/html/

**Apply**

**Save**

## Ngrok

*ngrok on työkalu, jonka avulla voi sisäverkossa olevasta palvelusta luoda tunnelin julkiseen internettiin. esim. GitHub pääsee jenkinsille kertomaan päivityksistä, tai haluat luoda ssh-tunnelin laittaaksesi kaupungilla/asioilla digiboxin  ajastukseen.*

- Mene Ngrok.com -sivulle ja rekisteröi ilmainen tunnus porttitunnelointia varten
- Lataa ngrok ohjelma "Get Started" -sivulta
- Pura ```ngrok-stable-linux-amd64.zip``` -tiedosto
- siirrä tiedosto hakemistoon: ```sudo mv ngrok /usr/local/bin/```
- Authorisoi tunnuksesi ```ngrok authtoken [token]```

*Linuxissa zip-paketti puretaan tällä komennolla* ```unzip ngrok-stable-linux-amd64.zip```


## Aloita tunneli


Jenkins on osoitteessa localhost:8080

Aloitetaan tcp-portti 8080 -tunneli 

Ajetaan Linuxin terminaalissa tämä komento

```ngrok tcp 8080```


Terminaaliin avautuu ohjelma, joka näyttää tcp-osoitteen:

> Forwarding                    tcp://0.tcp.ngrok.io:10464 -> localhost:8080

*ngrokin voi halutaessaan sulkea ctrl+c näppäinyhdistelmällä*

### Testaa osoite

Siirry siis selaimessa osoitteseen [http://0.tcp.ngrok.io:10464](http://0.tcp.ngrok.io:10464) riippuen mitä osoitetta ngrok-ohjelma näyttää.


## Asetetaan GitHub

Men oman GitHub repon sivulle esim https://github.com/lnxbusdrvr/mdfilesforhugo

Settings -> Webhook -> Add webhook

	Payload URL
		http://0.tcp.ngrok.io:10464/github-webhook/
	Content type
		application/json

*Eli /github-webhook/ -kohta laitetaan ngrok-osoitteen perään*
	

**Add webhook**


## Julkaistaan Jenkins URL

Jenkinsissa

Manage Jenkins -> Configure System -> 

	GitHub Pull request
		Published Jenkins URL
			git@github.com:kayttajatunnus/repo.git

**Apply**

**Save**


## reference

1. [Triggering a Jenkins build from a push to Github](https://medium.com/@marc_best/trigger-a-jenkins-build-from-a-github-push-b922468ef1ae)
1. [IP address of localhost:8080 -in webhooks of github +jenkins](https://stackoverflow.com/questions/46822898/ip-address-of-localhost8080-in-webhooks-of-github-jenkins)
1. [Public URLs for building webhook integrations.](https://ngrok.com/)
1. [Get Started](https://dashboard.ngrok.com/get-started)
1. [Adding a GitHub Webhook in Your Jenkins Pipeline](https://dzone.com/articles/adding-a-github-webhook-in-your-jenkins-pipeline)

