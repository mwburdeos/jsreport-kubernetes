#JSREPORT - Kubernetes
This repository demonstrates how JSREPORT can be used as a part of a Kubernetes
cluster.  This solution covers the following
* how to build JSREPORT as a pod that is deployable within a Kubernetes cluster
* how to run JSREPORT so that report templates can be created and editted
* pushing report updates to your Kubernetes cluster
* managing your JSREPORT pod as you would any other pod in your application



#Sample Markup:

#Install Oracle Java 8 and maven 3
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get install oracle-java8-installer
sudo apt-get install maven
```
#Install kde desktop *(Note: optional)*
Provides Konsole, used by mon.sh to launch a tabbed
terminal window to view services running in local cloud.

#Alternately, just install Konsole
`sudo apt-get install konsole`
#Install latest docker
```
curl -fsSL https://get.docker.com/ | sh
usermod -aG docker ${USER}
```
#Build images
This will sync all projects to a local directory and build them,
including building docker images.
`./buildImages.sh`
#Run setup.sh
This will do the following automatically:
- Install python3 pip (python's updater - similar to apt-get)
- Install pyyaml with pip (for reading yaml files with python)
- Install docker-compose
- Create a name 'dev.local' which points to the interface associated with the docker0 interface.
- Install the dev.local.crt certificate so that the web socket will be trusted locally in Chrome

#Testing Estimating locally
Estimating is accessible from `http://dev.local:8081`.

If you will be testing in Firefox, you need to trust the dev.local.crt certificate from within Firefox.
*Note: this is added simply to support trusting secure web sockets in Estimating application. For Chrome,
setup.sh installs the certificate automatically.*

Open Firefox and browse to `https://dev.local:61613`. Firefox will complain that the certificate is
not trusted. Add an exception for this untrusted provided certificate. Once the exception is added,
the page will show HTTP ERROR: 500, which looks like an error, but it can be safely ignored. Now
browse to `http://dev.local:8081` to start.
