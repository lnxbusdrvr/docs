
## Vagrant GCP CloudBuild in vagrant gcloud Terraform & Ansible

## Install VirtualBox

Install vagrant from their webpage:
(https://www.virtualbox.org/wiki/Downloads)

## Install vagrant

Install vagrant from their pagpage:
(https://www.vagrantup.com/downloads.html)


## Prepare to use Vagrant

open cmd.exe, or powershell, or terminal

```
mkdir vagrant
cd vagrant
```

## Get Vagrant Ubuntu desktop image & start vagrant

We are not in vagrant-direcrory which we just created:
Command this to get image:

```
vagrant init peru/ubuntu-18.04-desktop-amd64
```
**Start Vagrant**

```
vagrant up
```

## Install updates and programs

Open setting and change language to your fits.<br>
Install updates: <br>
```
sudo apt-get update
sudo apt-get upgrade
```
## Download terraform

Download Terraform from Terraform's webpage: <br>
In terminal do this: <br>
```
sudo apt-get install unzip
wget -c https://releases.hashicorp.com/terraform/0.11.13/terraform_0.11.13_linux_amd64.zip
```

So firstly we downloaded unzip-program and then we downloaded Terraform-app in .zip -file

unzip Terraform's .zip -file: <br>
```
unzip terraform/0.11.13/terraform_0.11.13_linux_amd64.zip
```

Now move t````terraform``` -file to binary location:<br>
```
sudo mv terraform /usr/local/bin
```

## Install ansible

```
sudo apt-get install ansible
```

## Make ssh-key

Make ssh-key to authorize to use git:

```
ssh-keygen
```

Copy content of ~/.ssh/id_rsa.pub <br>
You can see the content of the file by opening eg. with nano: <br>
```
nano ~/.ssh/id_rsa.pub
``` <br>
or with ```cat``` : <br>
```
cat ~/.ssh/id_rsa.pub
``` <br>

Copy the content of file with mouse

## Add your public ssh-key to GitHub

Go to (https://www.github.com/)
Log in <br>
In right of page there is your profile picture<br>
Click your profile-picture<br>
and click **Settings** <br>
In settings-page:
Click **SSH and GPG keys** <br>
Now click the green **New SSH key** -button <br>

Title:
    <enter name of your computer here>
Key:
    <content of your ~/.ssh/id_rsa.pub -file>

Click green **Add SSH Key** -button

TÄSTÄ ALAS KESKEN
## Clone .tf and ansible-files from your git repo

cd src
git clone <your_git_repo>

## Create Project in GCP (Google cloud)

Create new project in GCP


## EasyWay to authorize with GCP

login to GCP:

```
gcloud auth login
```

## HardWay to authorize with GCP

### Make credenials on GCP-page:

Make sure to use same project that you've created and will be using.
Home > API & Services > Credentials

Create Credential
Service account key

Service account:
    New account service

Service account name:
    terraform

Role:
    owner

Service account ID:
    terraform

key type
(*) JSON

**Create**

Save flie -window will pop-up

Save the .json

## Edit provider.tf

Beginning of ```project.tf``` looks like this:

```tf
provider "google" {
  credentials = "${file(".cred/serviceacct.json")}"
  project     = "inframimmit"
  region      = "${var.region}"
}
```tf

project = "inframimmit" should be your own project name

## Initialize Terraform

```
terraform init
```

## Test .tf-files

```
terraform plan
```

## Start terraform

```
terraform apply
``

"Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value:"

``` yes```


