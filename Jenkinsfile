node{

   def tomcatWeb = 'C:\\apache-tomcat-9.0.54\\webapps'
   def tomcatBin = 'C:\\apache-tomcat-9.0.54\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/shreyadey16/sample3.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     sh "scp -o StrictHostKeyChecking=no /var/jenkins_home/workspace/shreya-training/samp_pipe3/target/JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         sh "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
