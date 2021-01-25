pipeline {
    agent any

3    def tomcatWeb = 'C:\\tomcat\\webapps' 
4    def tomcatBin = 'C:\\tomcat\\bin' 
5    def mvnHome = 'C:\\maven' 
6    def tomcatStatus = '' 
7    stage('SCM Checkout'){ 
8      git 'https://github.com/mnreddy69/JenkinsWar.git' 
9    } 
10    stage('Compile-Package-create-war-file'){ 
11       // Get maven home path 
12 
 
13       bat "${mvnHome}\bin\mvn clean package" 
14       } 
15 /*   stage ('Stop Tomcat Server') { 
16                bat ''' @ECHO OFF 
17                wmic process list brief | find /i "tomcat" > NUL 
18                IF ERRORLEVEL 1 ( 
19                     echo  Stopped 
20                ) ELSE ( 
21                echo running 
22                   "${tomcatBin}\\shutdown.bat" 
23                   sleep(time:10,unit:"SECONDS")  
24                ) 
25 ''' 
26    }*/ 
27    stage('Deploy to Tomcat'){ 
28      bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\"" 
29    } 
30         stage ('Start Tomcat Server') { 
31          sleep(time:5,unit:"SECONDS")  
32          bat "${tomcatBin}\\stop.bat" 
33          bat "${tomcatBin}\\startup.bat" 
34          sleep(time:100,unit:"SECONDS") 
35    } 
}
