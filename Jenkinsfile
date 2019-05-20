pipeline {
  
  agent any  
  
  stages {
    stage('checkout') {
      steps {
        checkout scm
  	    }
    	}
    
 
    stage('Packer version') {
      steps {
        sh '/usr/bin/packer --version'
      }
    }
	
    stage('Image Build & Encrypt') {
      steps {
        sh '/usr/bin/packer build image.json'
	cleanWs()
      }
    }
  }
  
  post {  
         always {  
             echo 'This will always run'  
         }  
         success {  
             echo 'This will run only if successful'  
			 mail bcc: '', body: "<b>Packer AMI Build Status</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: 'shivayogi.mkamat@dimensiondata.com', mimeType: 'text/html', replyTo: '', subject: "SUCCESS CI: Project name -> ${env.JOB_NAME}", to: "yogisdmec007@gmail.com,smuttin@gmail.com"; 
         }  
         failure {  
             mail bcc: '', body: "<b>Packer AMI Build Status</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: 'shivayogi.mkamat@dimensiondata.com', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "yogisdmec007@gmail.com,smuttin@gmail.com";  
         }  
         unstable {  
             echo 'This will run only if the run was marked as unstable' 
             mail bcc: '', body: "<b>Packer AMI Build Status</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: 'shivayogi.mkamat@dimensiondata.com', mimeType: 'text/html', replyTo: '', subject: "UNSTABLE CI: Project name -> ${env.JOB_NAME}", to: "yogisdmec007@gmail.com,smuttin@gmail.com"; 			 
         }  
         changed {  
             echo 'This will run only if the state of the Pipeline has changed'  
             echo 'For example, if the Pipeline was previously failing but is now successful'  
			 mail bcc: '', body: "<b>Packer AMI Build Status</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: 'shivayogi.mkamat@dimensiondata.com', mimeType: 'text/html', replyTo: '', subject: "Pipeline status has changed CI: Project name -> ${env.JOB_NAME}", to: "yogisdmec007@gmail.com,smuttin@gmail.com"; 
         }  
     }  
  
  
}
