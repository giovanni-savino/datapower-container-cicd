# datapower-container-cicd
Example of updating Datapower in container with Ansible script

In order to update the Datapower, you need to:

* Deploy a first Datapower on a OCP namespace (eg dp-svil) and expose the REST API
* Deploy the second Datapower in a second namespace (eg dp-col)
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

