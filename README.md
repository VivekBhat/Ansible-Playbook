
# Configuration Management
  The goal of this project is to demonstrate how to use ansible to help us configure software. 

Here I have created 2 ansible playbooks that can be used to:

**Playbook 1 (hw.yml):**  
* **Setup:** Install the following items:
    * Install node.js
    * Install forever
    * Pull/clone git repo 
    * Install npm packages

* **Run Tasks :**
    * Run app: `forever start main.js`
    * Security: Ensures `bash`, `openssl`, `openssh-client`, and `openssh-server` are running latest version.
    * Cleanup: Remove content in `/tmp/*`

[Screencast](https://youtu.be/n2BykwcTUJ0) : This screencast shows how to perform the whole setup, run the defined tasks and the running app.
 
---

**Playbook 2 (aws.yml):**
* **Provision:** 
    A new virtual machine from a virtual machine provider Amazon EC2 is provisioned.

[Screencast](https://youtu.be/NEtXje9PKUk): This screencast shows how to perform provisioning of an Amazon Web Services EC2 instance.

---    

Locally I have created two Vagrant Machines following these steps

### Creating Virtual Machine

Install [vagrant](https://www.vagrantup.com/downloads.html).

You will also need a [virtual machine provider](https://docs.vagrantup.com/v2/providers/). [VirtualBox](https://www.virtualbox.org/wiki/Downloads) is a recommended provider.

Initialize a virtual machine. `ubuntu/trusty64` is one default image. A list of other virtual machine images can be found [here](https://atlas.hashicorp.com/boxes/search).

    vagrant init ubuntu/trusty64

Start up the virtual machine.

    vagrant up

Then    

    vagrant ssh



You should be able to connect to the machine.

### Configuration with Ansible

Ansible is a tool for configuring and coordinating software on multiple machines.
In general, Ansible (like Salt, Chef, and Puppet), use a central server that controls other nodes.  Unlike the other tools, Ansible does not require a client service to run on the nodes.

#### Let's setup some stuff first

We want to create a master server that runs Ansible. First, use a binary package manager to setup some basic stuff missing.

    sudo apt-get update
    sudo apt-get -y install git make vim python-dev python-pip libffi-dev libssl-dev libxml2-dev libxslt1-dev libjpeg8-dev zlib1g-dev

Now get ansible itself.

    sudo pip install ansible

Test ansible

    ansible all -m ping

**Note, you should not expect to see anything working, quite yet, this just makes sure, python, etc. is setup properly.**

----
