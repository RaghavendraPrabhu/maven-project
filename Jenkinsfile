pipeline {
    agent any
    stages {
        stage('Build'){
            steps{
                bat 'mvn clean package'
                bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"
				bat "docker run -p 8091:8080 --name tomcat_development tomcatwebapp:${env.BUILD_ID}"
				
				
            }
        }

    }
}