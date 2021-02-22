pipeline {
    agent any
    stages {
        stage('Build'){
            steps{
                bat 'mvn clean package'
                bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"
				bat "docker stop tomcat_development"
				bat "docker rm tomcat_development"
				bat "docker run -d -p 8091:8080 --name tomcat_development tomcatwebapp:${env.BUILD_ID}"
				
				
            }
        }

    }
}