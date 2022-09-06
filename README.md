# Oracle SQL INSTALLATION ON UBUNTU (debian) based systems.
### STEP 1: DOWNLOAD THE .zip file from the google drive link provided below.
```
  add google drive link here
```
### STEP 2: EXTRACT ALL THE FILES IN THE DOWNLOADS FOLDER (makes the process much easier.)
>Three files should be extracted namely jdk-17.0.4.1_linux-x64_bin.deb , oracle-xe_11.2.0-2_amd64.deb , sqldeveloper-22.2.0.173.2018-no-jre.zip

##Step 3:  SETTING UP THE PREREQUISITES:
a) Open Up your terminal and type the following command followed by your password:\
\
```sudo gedit /sbin/chkconfig```\
>After successfully running the command a text editor should open up.

b) Paste the following text in the file and save it.\
<br/>
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
```chmod 755 /sbin/chkconfig``` <br/>
<br/>
d) Setting up kernal parameters:<br/> 
<br/>
```sudo gedit /etc/sysctl.d/60-oracle.conf```
<br/>
<br/>
> Again text editor should open up and you have to enter the following text in the file : <br/>
> <br/>
```
# Oracle 11g XE kernel parameters  
fs.file-max=6815744  
net.ipv4.ip_local_port_range=9000 65000  
kernel.sem=250 32000 100 128 
kernel.shmmax=536870912 
```
<br/>
<br/>

e) Load new kernal parameters by entering :
<br/>
<br/>
```sudo service procps start```
<br/>
<br/>

f) Some more changes :
<br/><br/>
```ln -s /usr/bin/awk /bin/awk```
<br/>
```mkdir /var/lock/subsys```
<br/>
```touch /var/lock/subsys/listener```
<br/>
<br/>

## STEP 4: INSTALLING Oracle 11 XE (by opening terminal in the downloads folder) :
<br/><br/>
```sudo dpkg --install oracle-xe_11.2.0-2_amd64.deb```
<br/><br/>

## STEP 5 : AVOIDING 'MEMORY TARGET' ERROR.
  a)
<br/><br/>
```sudo mount -t tmpfs shmfs -o size=2048m /dev/shm```
<br/><br/>
  b)Create a file at the required location by:
```sudo gedit /etc/rc2.d/S01shm_load```
<br/><br/>
  c) Now copy and paste following lines into the file :
 ```
  #!/bin/sh
case "$1" in
start) mkdir /var/lock/subsys 2>/dev/null
       touch /var/lock/subsys/listener
       rm /dev/shm 2>/dev/null
       mkdir /dev/shm 2>/dev/null
       mount -t tmpfs shmfs -o size=2048m /dev/shm ;;
*) echo error
   exit 1 ;;
esac 
```
<br/><br/>
  d)Save the file and provide execute permissions :
  <br/><br/>
  ```sudo chmod 755 /etc/rc2.d/S01shm_load```
  <br/><br/>
  
### STEP 6: CONFIGURING ORACLE SQL 11 XE
<br/><br/>
```sudo /etc/init.d/oracle-xe configure```
<br/><br/>

> NOTE: PORTS SHOULLD BE SET TO DEFAULT NO CHANGES SHOULD BE MADE AND FOR THE MACHINES OWNED BY COLLEGE PASSWORD SHOULD BE SET TO 'admin' only

### STEP 7: ADDING ENVIRONMENT VARIABLES:
```cd /home```
<br/>
```sudo gedit ~/.bashrc```
<br/>
>A FILE SHOULD OPEN WITH SOME TEXT ALREADY WRITTEN IN IT PASTE THE FOLLOWING TEXT :
```
export ORACLE_HOME=/u01/app/oracle/product/11.2.0/xe
export ORACLE_SID=XE
export NLS_LANG=`$ORACLE_HOME/bin/nls_lang.sh`
export ORACLE_BASE=/u01/app/oracle
export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH
export PATH=$ORACLE_HOME/bin:$PATH
```
<br/><br/>


### STEP 8: RESTART THE MACHINE

### STEP 9 : START ORACLE 11 XE
```sudo service oracle-xe start```
<br/><br/>

### STEP 10 :
```sqlplus```



