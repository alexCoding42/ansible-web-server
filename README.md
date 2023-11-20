# Install httpd web server with Ansible and run html page

In this project, I configured a jump host server and installed Ansible, then I created 3 virtual machines and installed CentOS server on them. 
The jump host plays the role of the Ansible Controller, and virtual machines play the role of web servers where an Html page is supposed to run. 
![Cover](https://www.dropbox.com/scl/fi/g0xkjv49llkli0ogzuf2f/visual.png?rlkey=s39w1ua0krtm2yezml7cnqwdy&raw=1)

## Configuration

Inside the Ansible controller machine create a folder **ansible** and add a **inventory** file (look for the file in this project):

## Ping test

First, make sure you are under the **ansible** folder

```
cd ansible
```

To test that you can access the hosts from the Ansible controller run

```
ansible all -m ping -i inventory
```

The following result should follow if successful (note that the IP address will change for you)

```
192.168.33.10 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
192.168.33.11 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
192.168.33.12 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
```

## Install httpd on the web servers and run a html page

Under you **ansible** folder add a **playbook.yml** file with the same content as the *playbook.yml* of this project

Then run

```
ansible-playbook -i inventory playbook.yml
```

It should install httpd on all web servers and run the html page.
