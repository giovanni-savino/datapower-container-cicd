# datapower-container-cicd
Example of updating Datapower in container with Ansible script

In order to update the Datapower, you need to:

## Using Ansible
* Deploy a first Datapower on a OCP namespace (eg gw-dev) and expose the REST API
* Deploy the second Datapower in a second namespace (eg gw-col)
* On the local machine you need to install the following packages:
* Ansible, git, oc/kubectl, jq

The first script download_dp_playbook.yaml:
* call the REST API of the first Datapower (edit the yaml to change the REST API url).
* It downloads a single domain config and local files
* it unzip on /tmp directory
* Clone this git repo on the /tmp directory
* Update the service of the second datapower if the domain does not exists
* Create the two configmap of the config and local directory
* Push the new files on this git repo

The second ansible script update_dp_playbook.yaml:
* Clone the git repo on /tmp directory
* apply the 2 kubernetes configmap
* Apply the  datapower service yaml  on the second namespace

## Using Ansible Tower

In order to use Tower you need to:

* Configure OCP credential in the tower
* Configure the git credential in the tower
* Add the kubernetes collection to the tower

https://docs.ansible.com/ansible-tower/latest/html/userguide/credentials.html#openshift-or-kubernetes-api-bearer-token
