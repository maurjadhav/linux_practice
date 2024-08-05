# Installing Jenkins on Ubuntu 22.04

## Introdduction

Jenkins is an open-source automation server that automates the repetitive technical tasks involved in the continuous integration and delivery of software. Jenkins is Java-based, installed from Ubuntu packages or by downloading and running its web application archive (WAR) file — a collection of files that make up a complete web application to run on a server.

## Prerequisites

* One Ubuntu 22.04 server configured with a non-root sudo user and firewall by following the Ubuntu 22.04 initial server setup guide. We recommend starting with at least 1 GB of RAM. Visit Jenkins’s “Hardware Recommendations” for guidance in planning the capacity of a production-level Jenkins installation.
* Oracle JDK 11 installed, following our guidelines on installing specific versions of OpenJDK on Ubuntu 22.04 [Refer Here](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-22-04#installing-specific-versions-of-openjdk)

## Installing Jenkins

First, add the repository key to your system:
```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key |sudo gpg --dearmor -o /usr/share/keyrings/jenkins.gpg
```
The *gpg --dearmor* command is used to convert the key into a format that apt recognizes.

Next, let’s append the Debian package repository address to the server’s sources.list:
```bash
sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.gpg] http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

After both commands have been entered, run apt update so that apt will use the new repository.
```bash
sudo apt update
```

Finally, install Jenkins and its dependencies:
```bash
sudo apt install jenkins
```

## Starting Jenkins

Now that Jenkins is installed, start it by using systemctl:
```bash
sudo systemctl start jenkins.service
```

Since systemctl doesn’t display status output, we’ll use the status command to verify that Jenkins started successfully:
```bash
sudo systemctl status jenkins
```

If everything went well, the beginning of the status output shows that the service is active and configured to start at boot:
```bash
Output
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2022-04-18 16:07:28 UTC; 2min 3s ago
   Main PID: 88180 (java)
      Tasks: 42 (limit: 4665)
     Memory: 1.1G
        CPU: 46.997s
     CGroup: /system.slice/jenkins.service
             └─88180 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080
```