# Installing Maven on Ubuntu with tar file

## Set Up OpenJDK
* Start by updating the system package index with the following command:
  
```bash
sudo apt update
```
* Next, install the latest version of OpenJDK on your system:
  
```bash
sudo apt install default-jdk -y
```
##  Verify OpenJDK Version

```bash
java -version
```
## Download the Latest Maven Version
Go to the Maven download page and select the most recent Maven version from the Files section. Copy the link of the tar.gz file [Refer Here](https://maven.apache.org/download.cgi)

Launch the terminal and navigate to the /tmp directory.

Run the wget command

```bash
wget https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz -P /tmp
```
## Extract the Archive
Navigate to the /opt directory with the cd command. Next, run the following command to extract the archive:

```bash
sudo tar xf /tmp/apache-maven-*.tar.gz -C /opt
```
## Create a Symbolic Link
Once the extraction finishes, create a symbolic link named maven that points to the installation directory:

```bash
sudo ln -s /opt/apache-maven-3.9.6 /opt/maven
```

## Configure Environment Variables
Go to the /etc/profile.d/ directory, create and open the maven.sh script file in your preferred text editor. We will use the following command to create and edit the file in Vi:

```bash
sudo vi /etc/profile.d/maven.sh
```
Add the following export statement lines in the maven.sh file to make the script executable:

```bash
export JAVA_HOME=/usr/lib/jvm/default-java
export M2_HOME=/opt/maven
export MAVEN_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
```
Next, use the chmod command to give the maven.sh file executable permission:

```bash
sudo chmod +x /etc/profile.d/maven.sh
```
Run the following source command to load the configuration from the maven.sh file:

```bash
source /etc/profile.d/maven.sh
```

## Verify the Maven Installation

```bash
mvn -version
```