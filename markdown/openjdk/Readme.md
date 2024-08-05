# JAVA Installation with the tar file

* For downloading the JAVA tar file version [Refer Here](https://jdk.java.net/archive/)
  * Currently we are having the following java versions
      * 22
      * 21
      * 20
      * 19
      * 18

In this we are installing the JAVA 22.0.1 version avilable here [Refer Here](https://download.java.net/java/GA/jdk22.0.1/c7ec1332f7bb44aeba2eb341ae18aca4/8/GPL/openjdk-22.0.1_linux-x64_bin.tar.gz)

## go to the TMP directory and download the tar file
```bash
cd /tmp

wget https://download.java.net/java/GA/jdk22.0.1/c7ec1332f7bb44aeba2eb341ae18aca4/8/GPL/openjdk-22.0.1_linux-x64_bin.tar.gz
```

## create jdk directory
```bash
sudo mkdir /opt/jdk
```

## uncompress, change to your file name 
```bash
sudo tar -zxf openjdk-22.0.1_linux-x64_bin.tar.gz -C /opt/jdk
```

## check if files are there
```bash
ls /opt/jdk
```

## update alternatives so the command java point to the new jdk
```bash
sudo update-alternatives --install /usr/bin/java java /opt/jdk/jdk-22.0.1/bin/java 100
```

## update alternatives so the command javac point to the new jdk 
```bash
sudo update-alternatives --install /usr/bin/javac javac /opt/jdk/jdk-22.0.1/bin/javac 100
```

## check if java command is pointing to " link currently points to /opt/jdk/jdk-22.0.1/bin/java"
```bash
sudo update-alternatives --display java
```

## check if java command is pointing to " link currently points to /opt/jdk/jdk-22.0.1/bin/javac"
```bash
sudo update-alternatives --display javac
```

## check if java is running
```bash
java -version
```