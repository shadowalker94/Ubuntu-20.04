######## guide to intallations and commands ###############




 sudo route add -net 10.211.0.0/16 gw 10.193.3.240

    4  apt install net-tools
    5  sudo apt install net-tools
    6  sudo vi /etc/apt/sources.list
    7  sudo apt update 
    8  sudo apt install net-tools
    9  sudo apt install openssh-server
   10  netstat -tupln (for checking open ports)
   11  sudo apt update 
   12  sudo apt install virtual
   13  sudo vi /etc/apt/sources.list
   14  sudo apt upgrade
   19  ping www.google.com
   20  sudo apt install wget


##########################################################################################################################################
installation and pre-run commands:

1)install ubuntu first
2)sudo ip route add 10.211.0.0/16 via 10.193.3.240
3)sudo vi /etc/apt/sources.list
d+shift+g for remove all 
{

deb http://10.211.34.202/ubuntu/ focal main restricted
deb http://10.211.34.202/ubuntu/ focal-updates main restricted
deb http://10.211.34.202/ubuntu/ focal universe
deb http://10.211.34.202/ubuntu/ focal-updates universe
deb http://10.211.34.202/ubuntu/ focal multiverse
deb http://10.211.34.202/ubuntu/ focal-updates multiverse
deb http://10.211.34.202/ubuntu/ focal-backports main restricted universe multiverse
deb http://10.211.34.202/ubuntu/ focal-security main restricted
deb http://10.211.34.202/ubuntu/ focal-security universe
deb http://10.211.34.202/ubuntu/ focal-security multiverse

# deb http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
#
# deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
#
# deb http://archive.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
#
# deb http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
#
# deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner


}  esc and :wq (to excute)

4)sudo apt update
5)sudo apt upgrade
6)sudo apt install net-tools vim openssh-server
7)sudo vim /etc/rc.local
{
#!/bin/bash
sudo route add -net 10.211.0.0/16 gw 10.193.3.240
exit 0
}   esc and :wq (to excute)

8)sudo chmod u+x /etc/rc.local

#################################################################################################################################################

installation apps:

--Install JDK17
sudo mkdir /usr/lib/jvm
cd /usr/lib/jvm 
sudo cp ~/Downloads/jdk-17_linux-x64_bin.tar.gz  /usr/lib/jvm
sudo tar -xvzf ./jdk-17_linux-x64_bin.tar.gz
sudo vim /etc/environment

{
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/jdk-17/bin"
JAVA_HOME="/usr/lib/jvm/jdk-17"
} 	esc and :wq (to excute)

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk-17/bin/java" 0
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk-17/bin/javac" 0
sudo update-alternatives --set java /usr/lib/jvm/jdk-17/bin/java
sudo update-alternatives --set javac /usr/lib/jvm/jdk-17/bin/javac
update-alternatives --list java
update-alternatives --list javac
java -version

sudo rm -rf /usr/lib/jvm/jdk-17_linux-x64_bin.tar.gz

--Install dbeaver
cd ~/Downloads
sudo apt install ./dbeaver-ce_22.3.0_amd64.deb


--Install SQL Developer
sudo unzip -d /opt ~/Downloads/sqldeveloper-22.2.1.234.1810-no-jre.zip
sudo ln -s /opt/sqldeveloper/sqldeveloper.sh /usr/local/bin/sqldeveloper
sudo vim /opt/sqldeveloper/sqldeveloper.sh 
{
#!/bin/bash
/opt/sqldeveloper/sqldeveloper/bin/sqldeveloper $*

}	esc and :wq (to excute)

sudo vim /usr/share/applications/sqldeveloper.desktop

{

[Desktop Entry]
Name=Oracle SQL Developer
Comment=SQL Developer from Oracle
GenericName=SQL Tool
Exec=/usr/local/bin/sqldeveloper
Icon=/opt/sqldeveloper/icon.png
Type=Application
StartupNotify=true
Categories=Utility;Oracle;Development;SQL;


}	esc and :wq (to excute)




sudo rm -rf ~/Downloads/*
