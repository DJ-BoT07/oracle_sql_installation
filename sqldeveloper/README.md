# SQL DEVELOPER INSTALLATION UBUNTU 

### STEP 1: DOWNLOAD JAVA DEVELOPMENT KIT (place it in the downloads folder(easier)) :
```https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.deb```
>NOTE : JDK DEBIAN FILE IS ALREADY UPLOADED TO MY GOOGLE DRIVE , LINK IN MAIN PAGE'S README

### STEP 2: DOWNLOAD ORACLE SQL DEVELOPER (ALSO PRESENT IN THE DRIVE) , PLACE IT IN THE DOWNLOADS FOLDER:
```https://www.oracle.com/database/sqldeveloper/technologies/download/```

>DOWNLOAD THE FILE LISTED IN 'OTHER PLATFORMS' (might need to agree to TnC and login/create an Oracle Account)

### STEP 3: INSTALLING JAVA DEVELOPMENT KIT:
>OPEN TERMINAL IN DOWNLOADS FOLDER
```sudo dpkg -i jdk-17.0.4.1_linux-x64_bin.deb```
>CHECK FILE NAME IF ERROR POPS UP

### STEP 4: VERIFY JDK INSTALLATION:
```ll /usr/lib/jvm```
>OUTPUT
>total 12
>drwxr-xr-x   3 10668 10668 4096 Sep  2 10:51 ./
>drwxr-xr-x 117 root  root  4096 Sep 10 01:06 ../
>drwxr-xr-x   9 10668 10668 4096 Sep  2 10:56 jdk-17/

## STEP 5: INSTALLING SQL DEVELOPER<br/><br/>
  a) change directory to opt<br/><br/>
  ```cd /opt```<br/><br/>
  b) unzipping sqldeveloper.zip<br/>
  ```sudo unzip /home/ubuntu/Downloads/sqldeveloper-22.2.0.173.2018-no-jre.zip```<br/>
  >CHECK FILE NAME IF ERROR POPS <br/><br/>


  c) enter sqldeveloper folder in opt directory:<br/>
  ```cd /opt/sqldeveloper```<br/><br/>
  d)run script:<br/>
  ```./sqldeveloper.sh```<br/><br/>
  f)specify full path of jdk:<br/>
  ```/usr/lib/jvm/jdk-17```<br/><br/>
  g)application should startup<br/><br/><br/>

## STEP 6: CLOSE THE APPLICATION AND TERMINAL AND OPEN A NEW TERMINAL TO CREATE A SHORTCUT:
```sudo ln -s /opt/sqldeveloper/sqldeveloper.sh /usr/local/bin/sqldeveloper```
## STEP 7: CHANGE DIRECTORY AND EDIT sqldeveloper.sh file
```cd /opt/sqldeveloper```
<br/><br/>
```sudo gedit sqldeveloper.sh```
## STEP 8: REPLACE THE _**WHOLE**_ CONTENT OF FILE WITH THE FOLLOWING:
```
#!/bin/bash
/opt/sqldeveloper/sqldeveloper/bin/sqldeveloper $*
```
## STEP 9: _**SAVE**_ THE FILE AND RESTART THE MACHINE
<br/><br/>
## STEP 10: OPEN TERMINAL AND TYPE : sqldeveloper
>SQL DEVELOPER SHOULD START
