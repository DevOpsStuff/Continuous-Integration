# Continuous-Integration
CI and CD using Jenkins


https://github.com/effectivejenkins/myProject/blob/master/Jenkinsfile

https://gist.github.com/abayer/925c68132b67254147efd8b86255fd76

https://github.com/jenkinsci/pipeline-examples/tree/master/declarative-examples/simple-examples


```
Jenkins Architecture:
Jenkins Terms:
   * Nearly Everything is a Plugin
       * Build Tools
       * Integration
       * New Functionality
  * Default Plugins
  * Available Plugins

  * Projects == Jobs
  * CRON On Steroids
  *

Pre-requisites:
-> Java 1.7 or above

Installation Jenkins:

https://vexxhost.com/resources/tutorials/how-to-install-configure-and-use-jenkins-on-ubuntu-14-04/
https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04
https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-16-04

Install Maven on ubuntu:
https://www.vultr.com/docs/how-to-install-apache-maven-on-ubuntu-16-04

Jenkins service restarting:

service jenkins start

Continuous Inspection
  * Java Focused
      * Checkstyle
      * code updates

Plugins
->pmd
->findbugs
->checkstyle


Jenkins Slave

-> ON Master
   su jenkins -s /bin/bash
   ssh-keygen
   cd /var/lib/jenkins/.ssh/
   ssh -o HostKeyAlgorithms=ssh-rsa 172.28.128.5
   copy id_rsa.pub

-> on Slave
   useradd -d /var/lib/jenkins/ jenkins
   mkdir /var/lib/jenkins/.ssh
   chown -R jenkins:jenkins /var/lib/jenkins
   ssh -o HostKeyAlgorithms=ssh-rsa 172.28.128.3
   vi /var/lib/jenkins/.ssh/authorized_keys
   cp that public here

   And install java on slave and set the JAVA_HOME path



WorkSpace:

$BUILD_NUMBER
$NODE_NAME
$JOB_NAME
$EXECUTER_NAME
$WORKSPACE

GIT ENV Variable

$GIT_COMMIT
$GIT_BRANCH
$GIT_URL
$GIT_PREVIOUS_COMMIT

PARAMATERIZED Project
paramateized build triiger plugin

Jenkinsfile
-> Defines your continuous delivery pipeline
-> 2 styles - Declaritive and Scripted

def notify(status){
    emailext (
      to: "you@gmail.com",
      subject: "${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at <a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a></p>""",
    )
}

-> Parallel jenkins file


Plugins
-> PMD
-> FindBugs
-> Checkstyle
-> Junit
-> Htmlplublisher
-> Blue ocean


Common Types of Testing
-> Unit Testing
-> smoke Testing
-> Integration Testing
-> Acceptance Testing
-> Code Coverage(meta)

Unit Testing:
  Tests a small part of the code set. Usally associated with an indivial class if applicable.

Smoke Testin:
  Also Known as Sanity,Verification or Functional Testing
  It is a smaller subsets of tests that ensure that softwares primary functionality still works.
  After Unit Testing

Integration Testing
 Integration Testing ensures major units or modules all still work together.
 Happens after functional testing

Acceptance Testing
 Determines the overall acceptiablity of the software based on the business requirements.

Code Coverage
 Testing on the Testing
 Code coverage is a measure of the degree of tesing on ypur codeset.
 cobertura plugin for java,jaccaco



Jenkins CLI
http://www.tsbakker.nl/jenkins.html
```
