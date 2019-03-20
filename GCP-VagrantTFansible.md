
## Vagrant GCP CloudBuild in vagrant gcloud Terraform & Ansible

## Install VirtualBox

Install vagrant from their webpage:
(https://www.virtualbox.org/wiki/Downloads)

## Install vagrant

Install vagrant from their pagpage:
(https://www.vagrantup.com/downloads.html)

Download terraform from terraform netpage

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
## Install update and few programs

Open setting and change language to your fits.<br>
Install updates: <br>
```
sudo apt-get update
sudo apt-get upgrade
```
**TÄSTÄ ALASPÄIN KESKEN**
## Install ansible

```
sudo apt-get install ansible
```
## Clone tf and ansible-files

cd src
git clone <kodinterr>

## Create Project in GCP (Google cloud)

Create new project in GCP


## EasyWay to authorize

login to GCP:

```
gcloud auth login
```


## HardWay to authorize

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


