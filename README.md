# ubuntu-16-scripts
These are my current scripts that I'm using to setup my ubuntu server environments. Generally these are for the sake of learning and reference. 
Included so far: 
- Docker Installer (install-docker-ce)
- Git Installer (install-git)

# install-git
To install git, first copy the script to the remote server, and then run the install-git script as root.

1. Copy the script to the remote server.
```
cd <path-to-this-repository>
scp install-git <username>@<server-address>:/home/username/
```
2. Connect to the remote server
```
ssh <username>@<server-address>
```
3. Run the script
```
sudo ./install-git
```

# install-docker
1. Copy the script to the remote server.
```
cd <path-to-this-repository>
scp install-docker-ce <username>@<server-address>:/home/username/
```
2. Connect to the remote server
```
ssh <username>@<server-address>
```
3. Run the script
```
sudo ./install-docker-ce
```