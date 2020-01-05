#some test vagrant docker
Creates ubuntu systems to build then run docker image

* uses ansible for cm
* pulls opensource repo (randomly selected that has .war)
* archives docker image to local host
* deploys docker image to other system
* sends log to syslog
* TODO: monitor syslog for text 'hello.war'
* TODO: email notifyier based on above
