Download the tar file from https://www.keycloak.org/<br>
<br>#update the newly install RHEL Server and reboot<br>dnf update && dnf upgrade rhel 9<br>reboot server 

#copy over the file using your prefer method<br>sc or sftp the tar file to the rhel 9 

#it is best practice to create an account for keycloak<br>sudo useradd -r -s /sbin/nologin keycloak<br># -r is a system account -s /sbin/nologi is that user cannot log in interactively<br>#mover the file to the opt/keycloak directory and change the permissions<br>sudo chown -R keycloak:keycloak /opt/keycloak

#commmand to search what openjdk packeges are available I recommand doing another clean and update<br>sudo dnf search openjdk
<br>sudo dnf clean all && sudo dnf update

#install the java packake<br>sudo dnf install java-xx-openjdk-devel

#check to see if the firewall is running then add the port make it permanent and reload firewall<br> firewall-cmd --list-all<br>sudo firewall-cmd --add-port=8080/tcp --permanent<br>sudo firewall-cmd --reload

#set your server host name<br>sudo hostnamectl set-hostname <new_hostname><br>

#berfore starting keycloak set an environment variable with a desired password<br>export KEYCLOAK_ADMIN_PASSWORD='password you want to use"<br>#then run bootstrap-admin and tell it to read from that env var<br>bin/kc.sh bootstrap-admin user --username admin --password:env KEYCLOAK_ADMIN_PASSWORD --optimized

#Start Keycloak<br> bin/kc.sh start-dev

#log in to the admin console<br>http://serverIP:8080

