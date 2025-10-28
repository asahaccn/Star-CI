Troubleshooting guide :


Solution to common issues face by users while implementing ultimate CICD project



Error 1: 
[ERROR] Failed to execute goal org.sonarsource.scanner.maven:sonar-maven-plugin:4.0.0.4121:sonar (default-cli) on project spring-boot-demo: Execution default-cli of goal org.sonarsource.scanner.maven:sonar-maven-plugin:4.0.0.4121:sonar failed: An API incompatibility was encountered while executing org.sonarsource.scanner.maven:sonar-maven-plugin:4.0.0.4121:sonar: java.lang.UnsupportedClassVersionError: org/sonar/batch/bootstrapper/EnvironmentInformation has been compiled by a more recent version of the Java Runtime (class file version 61.0)

Cause : This error means the sonarqube server which is 10.4 version supports java 17 and above but we have the code compatible with java 11 

Solution : Downgrade sonarqube server to 9.x.x. to be compatible with java 11


Error 2:
[ERROR] 08:26:46.313 SonarQube server [http://<ec2-public-ip>:9000/] can not be reached
   
Cause : jenkins not able to connect with sonarqube server

Solution :

Check the sonarqube URL given in jenkinsfile it should be http://<public-ec2-ip>:9000
Check port 9000 is open under inbound rules of EC2 Sg
Check access to sonarqube from browser is up or not http://<public-ec2-ip>:9000
Check jenkins integrations with sonarqube. In jenkins UI go to manage jenkins > credentials > global credentials > system >  then select secret text, provide secret (token generated in sonarqube server), and make sure scope is set to global(jenkins item, child, all nodes item)
Check sonaqube logs for error (tail -n 50 /opt/sonarqube/sonarqube-9.9.8.100196/logs/sonar.log | grep -I error)
telnet 56.155.132.194 9000 // to check able to connect to sonarqube
ps -ef | grep sonar (to check all the process related to sonar is current instance)
netstat -tulnp 9000 (Active Internet connections (only servers))
systemctl status sonar.service // check sonar.service is running ore not 
vim /etc/systemd/system/sonar.service // check User=sonarqubee and Group=sonarqube if not change it
Run below linux commands to check whether sonarqube is up and running in your ec2 instance:
systemctl daemon-reload // reload the deamon after configuration changes are made
systemctl stop  sonar.service // stop the service
systemctl start  sonar.service // start the service
systemctl status sonar.service // show status of the service
