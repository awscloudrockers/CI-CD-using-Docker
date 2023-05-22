pipeline {
    agent any
	
	  tools
    {
       maven "Maven"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/awscloudrockers/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
          }
        }
         
      stage('Run Docker container on Jenkins Agent') {
             
            steps {
                sh "docker run -d -p 8003:8080 samplewebapp"
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://ec2-user@54.210.44.229 run -d -p 8003:8080 samplewebapp"
 
            }
        }
    }
}
    
