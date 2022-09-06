# Oracle SQL INSTALLATION ON UBUNTU (debian) based systems.
### STEP 1: DOWNLOAD THE .zip file from the google drive link provided below.
```
  add google drive link here
```
### STEP 2: EXTRACT ALL THE FILES IN THE DOWNLOADS FOLDER (makes the process much easier.)
>Three files should be extracted namely jdk-17.0.4.1_linux-x64_bin.deb , oracle-xe_11.2.0-2_amd64.deb , sqldeveloper-22.2.0.173.2018-no-jre.zip

## Setting Up Prerequisits:
a) Open Up your terminal and type the following command followed by your password:\
\
```sudo gedit /sbin/chkconfig```\
>After successfully running the command a text editor should open up.

b) Paste the following text in the file and save it.\
\
```
#!/bin/bash
# Oracle 11gR2 XE installer chkconfig hack for Ubuntu
file=/etc/init.d/oracle-xe
if [[ ! `tail -n1 $file | grep INIT` ]]; then
echo >> $file
echo '### BEGIN INIT INFO' >> $file
echo '# Provides: OracleXE' >> $file
echo '# Required-Start: $remote_fs $syslog' >> $file
echo '# Required-Stop: $remote_fs $syslog' >> $file
echo '# Default-Start: 2 3 4 5' >> $file
echo '# Default-Stop: 0 1 6' >> $file
echo '# Short-Description: Oracle 11g Express Edition' >> $file
echo '### END INIT INFO' >> $file
fi
update-rc.d oracle-xe defaults 80 01
```

c) Change privilege by executing the following command:\
\
```chmod 755 /sbin/chkconfig``` \

d) Setting up kernal parameters:<br/> 
```sudo gedit /etc/sysctl.d/60-oracle.conf```

       
 
