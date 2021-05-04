
# Creating single node kubernetes cluster with vagrant and ansible

- Install ansible on host
    ```
        curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
        python3 get-pip.py --user
        python3 -m pip install --user ansible
        python3 -m pip install --user paramiko
    ```
- Add ansible* binaries to PATH
    ```
        export PATH=$PATH:~/Library/Python/bin
    ```
- git clone github.com/bchannak/vagrant-k8s-ansible master
- cd master
- vagrant up
  - Creation of 'master' VM
  - Playbook is run from host to setup a basic kubernetes cluster
- vagrant ssh
- Verify the following:
  - kubectl get ns
  - kubectl get pods -n kube-system
- Copy contents of /home/vagrant/.kube/config to 
  ~/.kube/config to be able to access cluster from host
- Run a few sample applications and verify access to app in cluster:
  - dnsutils
  - nginx
  - httpbin
- Notes:
  - When using *vagrant destroy* to recreate VM, make sure to run *ssh-add -D* to clear ssh key from ssh-agent


# References
- [Install Ansible on OS X](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#from-pip)
- 