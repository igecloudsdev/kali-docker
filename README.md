# smartspaces-kali

![language](https://img.shields.io/github/languages/top/igecloudsdev/smartspaces-kali)    ![License](https://img.shields.io/github/license/igecloudsdev/smartspaces-kali)    ![Last Commit](https://img.shields.io/github/last-commit/igecloudsdev/smartspaces-kali)     ![FileCount](https://img.shields.io/github/directory-file-count/igecloudsdev/smartspaces-kali)    ![Stars](https://img.shields.io/github/stars/igecloudsdev/smartspaces-kali)    ![Forks](https://img.shields.io/github/forks/igecloudsdev/smartspaces-kali)

A Docker solution for running a local, customizable full Kali Linux distribution.

Configure the container with the following options:

- Exposed ports (vnc, x2go, rdp, ssh)
- Desktop environment(xfce, kde, gnome, mate, etc.)
- Remote access software (vnc, x2go, rdp)
- Kali packages to install (core, default everything, etc.)
- Network configuration  (host, bridge)
- Build platform (amd64, arm64, etc.)
- Local Docker image name
- Docker container name
- Host directory to mount as volume
- Container directory for volume mount
- Container username
- Container user password

## how to build

Download all the files into a subdirectory on Docker host, e.g. /home/marc/kali-linux docker
then cd into that directory. 

Create a copy of the `env_template` file, and name it `env`. Enter the desired configuration for each variable.

Run the build script:

    `sudo ./build`

If a variable isn't set in the `env` file, the build script asks for all the options then:
1. builds the local Docker image
2. Creates the container from the created image
3. Starts the new container

So in a nutshell, the complete command sequence in a Linux shell to install on a Debian or Ubuntu Linux would be:

    apt update
    apt install git
    git clone https://github.com/ecampuslearning/smartspaces-kali.git
    cd smartspaces-kali
    cp env_template env
    [fill_in_env_variables]
    sudo ./build

## how to use

Connect to the container by launching the software for the configured remote access technique or via SSH. The default ports defined in the script are as follows:

- RDP on port 13389
- ssh / x2goserver on port 20022
- vnc on port 5908 / display :8

All user name and password are configured in the `env` file or promted by the build script.

## known issues

- RDP seems to only work with XFCE desktop
- Not all combinations of remote access protocols with various desktop environments are working

## troubleshooting/tips
- When using RDP and XFCE, the desktop will take a moment to load the first time (about five seconds or less)

## TODO

- Disable desktop sleep, screenlock, etc.
