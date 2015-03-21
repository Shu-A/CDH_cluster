# CDH_cluster for Google Compute Engine
Make CDH cluster environment with ansible.

## Vagrant version
```
$ vagrant version
Installed Version: 1.7.2
Latest Version: 1.7.2

You're running an up-to-date version of Vagrant!
```

## Install dotenv and gcp vagrant puglin
```
$ vagrant plugin install dotenv
$ vagrant plugin install vagrant-google
```

## Set environment variables
```
$ GOOGLE_CLOUD_PROJECT_ID=xxx
$ SERVICE_ACCOUNT_EMAIL_ADDRESS=xxx
$ PATH_TO_YOUR_PRIVATE_KEY=xxx
```
## Execution
```
$ vagrant up --provider=google
$ vagrant ssh-config >> ~/.ssh/config
$ ansible-playbook -i ansible/production ansible/site.yml
```
### Install Cloudera Manager
```
$ ssh shua-cdh0
```

On shua-cdh0...

```
$ sudo ./cloudera-manager-installer.bin --i-agree-to-all-licenses --noprompt --noreadme
```
