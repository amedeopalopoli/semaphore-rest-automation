# Semaphore-Rest-Automation
> **An easy-to-use Ansible playbook to set up a Semaphore Tenant through its own REST APIs**.
----

The Ansible playbook is going to reference a Semaphore REST API server by creating/updating a set of **semaphore objects** through REST APIs. The ansible application logic is placed on a **Git Repo** from which you should provide **Oauth2** personal access token to login on.

----

### **Aim**

[Ansible](https://www.ansible.com/) is an open source automation and orchestration tool for software provisioning, configuration management, and software deployment.

Nevertheless, it's a good practice to integrate **playbooks** with UI systems and provide a smart workflow to even users who prefers better to interact with a UI based interface to invoke their own jobs.

[Ansible Semaphore](https://ansible-semaphore.com/) is a responsive web UI for running Ansible playbooks. It's written in pure Go and available for Windows, macOS and Linux (x64, ARM, ARM64). Furthermore, it provides a set of REST interfaces to make easier the way you can interact with the backend system in order to automate workflows. 

Therefore, the aim of this project is to provide a starter playbook to automate your own **Semaphore Tenant** with its own REST APIs. All this stuff is based on Ansible as well.

### **Dependencies**
----
1. [Ansible](https://www.ansible.com/) - Configuration Management
2. [Ansible Semaphore](https://ansible-semaphore.com/) -Ansible Modern UI - to set up follow this [guide](https://docs.ansible-semaphore.com/administration-guide/installation)
3. [OAuth Git Repo](https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps) - be sure to create an **access token** allowed to clone the repo where you store your own playbooks to be running towards your infrastructure target.
4. [Semaphore User](https://docs.ansible-semaphore.com/administration-guide/configuration) - allowed to perform REST calls towards the REST API Server
### **Configuration**
----

1. Clone the Repo
> **$ git clone https://github.com/amedeopalopoli/semaphore-rest-automation.git**

2. Locate the configuration file
> **$ cat vars/main.yml**

Point out your Semaphore REST API Server as reported below in **yourautomationurl**
```
# OVERALL VARIABLES

#Base URL Semaphore REST API Server -> <FQDN>/api
automation: "https://yourautomationurl/api"

```
Here, you are the security credentials to login through OAuth protocol to your own Semaphore REST API

```
#Basic Auth to Login to REST API Semaphore Server
user: "username"
password: "password"
```

After you earned the personal access token from your Git repo place that one here

```
#Personal Access Token to clone the code from your Ansible Repo
pat: "your_personal_access_token" 
git_repo: "gitlab.com/your_repo.git"
```

In order to use an OAuth2 git login the security key store with Semaphore is enough to use the **None** Security Keys Store Type

```
#Semaphore Key Type to clone the code through OAUTH2 Personal Access Token
semaphore_key_store_name: "None"
semaphore_key_store_type: "none"
```

Here, you are the application specific properties to customize your needs with the environments you have. Notice, how you can select even the cron format to run automatically your jobs for scheduling batch activities like backup and so on.

```
## PROJECT SPECIFIC VARIABLES
project_id: "semaphore_example"

envs:
  - name: develop
    cron: "0 0 * * *"
  - name: staging
    cron: "0 0 * * *"
  - name: production
    cron: "0 0 * * *"
```

### **Contributing**
----
1. Fork the repository
2. Create a new branch
3. Contribute!
4. Open a pull request

Obviously is ok if you want to improve the content and similar things. Whatever you think would be changed, feel free to open and issue and lets discuss it before. 

