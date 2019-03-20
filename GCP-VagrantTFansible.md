
## CloudBuild in vagrant GCP Terraform

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

Download Terraform from Terraform's webpage <br>
In terminal do this: <br>
```
sudo apt-get install unzip
wget -c https://releases.hashicorp.com/terraform/0.11.13/terraform_0.11.13_linux_amd64.zip
```

So firstly we downloaded unzip-program and then we downloaded Terraform-app in .zip -file

unzip Terraform's .zip -file: <br>
```
unzip terraform_0.11.13_linux_amd64.zip
```

Now move ```terraform``` -file to binary PATH:<br>
```
sudo mv terraform /usr/local/bin/
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
nano ~/.ssh/id_rsa.pub<br>
``` 
or with ```cat``` : <br>
```
cat ~/.ssh/id_rsa.pub
```

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
    <paste content of your ~/.ssh/id_rsa.pub -file>

Click green **Add SSH Key** -button


## Install GCloud


Create environment variable for correct distribution: <br>
```
export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)"
```

Add the Cloud SDK distribution URI as a package source: <br>
```
echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
```

Import the Google Cloud Platform public key: <br>
```
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

```
Finally install the app: <br>
```
sudo apt-get update ; sudo apt-get install google-cloud-sdk
```
## Create project directory in your vagrant machine

Create project dir: <br>
```
mkdir -p ~/src/terraform/.secret
```
Enter the terraform -directory: <br>
```
cd ~/src/terraform
```

## Create Project in GCP (Google cloud)

Create new project in GCP


## EasyWay to authorize with GCP

In vagrant machine terminal
login to GCP:

```
gcloud auth login
```
Firefox/Chrome opens a google login-page<br>
Accept all things

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

Save the .json -file or it's content <br>
to ``` ~/src/terraform/.security ``` -directory <br>
Name it as: ```serviceaccount.json```

**TÄSTÄ ALAS EI OLE TESTATTU**
## Edit provider.tf

```provider.tf``` looks like this:

```
provider "google" {
  credentials = "${file(".security/serviceaccount.json")}"
  project     = "inframimmit"
  region      = "${var.region}"
}
```

## Edit gkecluster.tf

```gkecluster.tf``` looks like this:

```
resources "google.container_cluster" "primary" {
  name			= "kubernetes-cluster" #This can named as whatever you want
  network		= "default"
  zone			= "europe-north1-b"
  initial_node_count	= 3
}
```

project = "inframimmit" should be your own project name

**Initialize Terraform**

```
terraform init
```

**Test .tf-files**

```
terraform plan
```

**Start Terraform**

```
terraform apply
```

"Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only yes will be accepted to approve.

  Enter a value:"

``` yes```


***ANSIBLE STUFF I DO LATER, WHEN I GET IT TO WORK***

