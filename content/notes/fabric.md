---
title: "Fabric"
draft: false
---

## Managing servers with Fabric ##

Fabric is a Python library for managing servers. If you find yourself setting up Raspberry Pi's a lot, it's a good tool for recreating the customizations that you like without having to remember all the details yourself.

## Installation ##

You should install Fabric on your laptop with `pip3`. To do this on Windows, you will first have to install the Windows Subsystem for Linux, also known as WSL2. (If you have been putting this off, just do it now.)

Here's what the installation should look like.

```
pip3 install fabric
Collecting fabric
  Downloading fabric-2.6.0-py2.py3-none-any.whl (53 kB)
     |████████████████████████████████| 53 kB 1.2 MB/s
Collecting invoke<2.0,>=1.3
  Downloading invoke-1.5.0-py3-none-any.whl (211 kB)
     |████████████████████████████████| 211 kB 6.0 MB/s
Collecting paramiko>=2.4
  Downloading paramiko-2.7.2-py2.py3-none-any.whl (206 kB)
     |████████████████████████████████| 206 kB 14.6 MB/s
Collecting pathlib2
  Downloading pathlib2-2.3.5-py2.py3-none-any.whl (18 kB)
Collecting bcrypt>=3.1.3
  Downloading bcrypt-3.2.0-cp36-abi3-manylinux2010_x86_64.whl (63 kB)
     |████████████████████████████████| 63 kB 2.4 MB/s
Requirement already satisfied: pynacl>=1.0.1 in /usr/lib/python3/dist-packages (from paramiko>=2.4->fabric) (1.3.0)
Requirement already satisfied: cryptography>=2.5 in /usr/lib/python3/dist-packages (from paramiko>=2.4->fabric) (2.8)
Requirement already satisfied: six in /usr/lib/python3/dist-packages (from pathlib2->fabric) (1.14.0)
Collecting cffi>=1.1
  Downloading cffi-1.14.5-cp38-cp38-manylinux1_x86_64.whl (411 kB)
     |████████████████████████████████| 411 kB 10.9 MB/s
Collecting pycparser
  Downloading pycparser-2.20-py2.py3-none-any.whl (112 kB)
     |████████████████████████████████| 112 kB 25.5 MB/s
Installing collected packages: invoke, pycparser, cffi, bcrypt, paramiko, pathlib2, fabric
Successfully installed bcrypt-3.2.0 cffi-1.14.5 fabric-2.6.0 invoke-1.5.0 paramiko-2.7.2 pathlib2-2.3.5 pycparser-2.20
```

## Usage ##

First, burn a new SD card, change the root password, and get your Pi on the internet. Fabric connects over SSH, so you have to be able to connect via SSH for any of this to work.

Here's an example script.

```python
from fabric import task

# Usage
#
# fab -H pi@192.168.1.217 --prompt-for-login-password deploy

@task
def deploy(c):
    hostname = c.run('hostname', hide=True).stdout
    print('\033[32;1mLogged into {0}\033[0m'.format(hostname))

    for package in DEBIAN_PACKAGES_TO_INSTALL:
        install_debian_package(c, package)

    for module in PYTHON_MODULES_TO_INSTALL:
        install_python_module(c, module)

    install_config_files(c)

    print('Deployment complete. Rebooting...')
    c.sudo('reboot')

def install_python_module(c, module):
    print('\nInstalling Python module: {0}'.format(module))
    c.run('pip3 install ' + module)

def install_debian_package(c, package):
    print('\nInstalling package: {0}'.format(package))
    c.sudo('DEBIAN_FRONTEND=noninteractive apt install -y ' + package)

def install_config_files(c):
    print('Copying over config files . . .')
    c.put('vimrc', '/home/pi/.vimrc')
    c.put('gitconfig', '/home/pi/.gitconfig')
    c.put('issue', '/etc/issue')
    c.put('issue.sh', '/etc/profile.d/issue.sh')

PYTHON_MODULES_TO_INSTALL = [
    'flask',
    'pysolar'
]

DEBIAN_PACKAGES_TO_INSTALL = [
    'htop'
]
```

