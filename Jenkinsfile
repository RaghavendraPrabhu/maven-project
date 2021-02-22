pipeline {
    agent any
    stages {
        stage('Build'){
            steps{
                bat 'mvn clean package'	

				//echo "current build number: ${currentBuild.number}"
                //echo "previous build number: ${currentBuild.previousBuild.getNumber()}"				
				
            }
        }
		
		stage ('Dockerise_Development'){
			steps{
                //bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"
				//bat "docker run -d -p 8091:8080 --name tomcat_development tomcatwebapp:${env.BUILD_ID}"
				
				//bat "docker build . -t tomcatwebapp:${currentBuild.number}"
				//bat "docker stop tomcat_development"
				//bat "docker rm tomcat_development"
				//bat "docker tag tomcatwebapp:${currentBuild.previousBuild.getNumber()} tomcatwebapp:backup"
				//bat "docker rmi tomcatwebapp:${currentBuild.previousBuild.getNumber()}"				
				//bat "docker run -d -p 8091:8080 --name tomcat_development tomcatwebapp:${currentBuild.number}"
				
				bat "docker build . -t tomcatwebapp_dev:${currentBuild.number}"				
				bat "docker stop tomcat_dev"
				bat "docker rm tomcat_dev"
				bat "docker tag tomcatwebapp_dev:${currentBuild.previousBuild.getNumber()} tomcatwebapp_dev:backup"
				bat "docker rmi tomcatwebapp_dev:${currentBuild.previousBuild.getNumber()}"
				bat "docker run -d -p 8091:8080 --name tomcat_dev tomcatwebapp_dev:${currentBuild.number}"			
			}
		}
		
		stage ('Dockerise_Production'){
			steps{				
				//bat "docker build . -t tomcatwebappprod:${currentBuild.number}"
				//bat "docker stop tomcat_production"
				//bat "docker rm tomcat_production"
				//bat "docker tag tomcatwebapp:${currentBuild.previousBuild.getNumber()} tomcatwebapp:backup"
				//bat "docker rmi tomcatwebapp:${currentBuild.previousBuild.getNumber()}"				
				//bat "docker run -d -p 8092:8080 --name tomcat_production tomcatwebapp:${currentBuild.number}"
				
				bat "docker build . -t tomcatwebapp_prod:${currentBuild.number}"
				bat "docker stop tomcat_prod"
				bat "docker rm tomcat_prod"
				bat "docker tag tomcatwebapp_prod:${currentBuild.previousBuild.getNumber()} tomcatwebapp_prod:backup"
				bat "docker rmi tomcatwebapp_prod:${currentBuild.previousBuild.getNumber()}"
				bat "docker run -d -p 8092:8080 --name tomcat_prod tomcatwebapp_prod:${currentBuild.number}"
			
			}
		}

    }
}