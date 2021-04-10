pipeline {
    agent any
    environment {
       PATH = "%PATH%;%MAVEN_HOME%\\bin"
    }
    
    stages {
     stage('Checkout Code') {
         steps {
            git 'https://github.com/irsal-yunus/RestAPiSwagerSample.git'
         }
      } 
     stage('Run Unit Test Cases') {
         steps {            
            bat "mvn.cmd clean test"
         }
     } 
     stage('Publish Test Reports') {
         steps {
            junit '**/target/surefire-reports/TEST-*.xml' 
         }
     }
     stage('Build Code') {
         steps {
            bat "mvn.cmd package -DskipTests=true" 
         }
     }
     stage('Archieve Result') {
         steps {
            archiveArtifacts 'target/*.war'  
         }
     }

   }
     
}
