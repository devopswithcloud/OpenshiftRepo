## Openshift Software Types
There are two types of openshift 
* Community Edition aka Origin Kubernetes Distribution (OKD)
*  Enterprise Edition aka Openshift Cotainer Platform (OCP) 

### Deployment Types
There are two deployment Types for Enterprise version of Openshift aka Openshift Container 
Platform (OCP) 

* Managed Services (deployed on AWS, Azure or IBM Cloud)
* Run it yourself (AWS, Azure, Google, or Platform agnostic) 

###  Installation Types (IPI & UPI)
For Run it yourself deployment type, there are two type of installers
* Installer-Provisoed Infrastructure (IPI)
* User-Provisioned Infrastrucuture (UPI)

## PreRequiste:
```Create a AWS Account ```

### Subscription to Redhat

* Go to https://developers.redhat.com/
* Click on Join Redhat Developer at the bottom of the page.
* Register by providing the details and verify your account
* Next Click on Profile icon , and click on ```Subscriptions```
* In the same browser go to this url ```https://console.redhat.com/``` If asked do fill the form.
* Click on Openshift

### Register a Domain 
* Register a domain name in any Register. Use ```freenom.com``` if you want to have a free domain name(but not suggestable as it may have few issues)
* Now once the registration is done, next step map the domain to aws ```route 53```

### Register DNS Entries for the Nameservers in AWS
* Go to the Route 53 on your AWS Console
* Click on the Hosted Zones
* Click on Create Hosted Zones
* Under Hosted zone configuration paste your Domian name which you created from in the ```previous step``` and select public Hosted zones in Type and Create Hosted zones
* Select the Record name and then copy the values
* Go to your registar where you created the domain. 
* go to dns 
* Update Nameservers which are generated as part of the route 53 , dns creation process.

### Creating and Launching an EC2 Instance
### Create a user 
* useradd siva
* passwd siva
* vi /etc/ssh/sshd_config
* systemctl restart sshd.service
* usermod -aG wheel siva
* Open putty or any terminal and then try to login to the user with the password created above.

### Create an IAM User

* aws configure
* us-east-2
* json

### Installation
Install my-project with npm

```bash
oc help
oc create --help
oc image --help
oc adm --help # For administration commands
```

### Installing on AWS
```bash
aws configure

ssh-keygen -t ed25519 -N '' -f ~/.ssh/id_rsa
mkdir ocp
cd ocp
# download the OCP Installer
wget https://mirror.openshift.com/pub/openshift-v4/x86_64/clients/ocp/stable/openshift-install-linux.tar.gz
tar xvf openshift-install-linux.tar.gz

# Download the OC Client
wget https://mirror.openshift.com/pub/openshift-v4/x86_64/clients/ocp/stable/openshift-client-linux.tar.gz
cp oc kubectl /usr/bin/


# Create the Install Config 
./openshift-install create install-config --dir=/root/ocp

./openshift-install create cluster --dir=/root/ocp --log-level=info

./openshift-install create destroy --dir=/root/ocp --log-level=info
```