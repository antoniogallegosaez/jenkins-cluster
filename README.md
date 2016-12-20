# jenkins-dynamic-cluster
Templates for creating a dynamic Jenkins cluster in OpenShift.

It combines these two repos to get an updated Jenkins dynamic cluster:
* https://github.com/siamaksade/jenkins-s2i-example
* https://github.com/sabre1041/ose-jenkins-cluster

Steps for implementation:

* Create a project in OpenShift: oc create new-project jenkins
* Give default user permission to edit the project: oc policy add-role-to-user edit system:serviceaccount:jenkins:default
* Create the two templates on the project: oc create -f jenkins-master-s2i-template.yaml,jenkins-swarm-slaves-template.yaml
* Add first the master node, and then add the slave node. In case Jenkins master is already running on the project, ensure that it has the Swarm plug-in installed.
