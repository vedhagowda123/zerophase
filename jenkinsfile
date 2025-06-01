#SonarQube: (t2.medium)
URL --->

username: admin
password: admin

after login change password

#create tokens in sonarqube
Administration -- security--user--update tokens--name--generate

#create credential in jenkin and add sonarqube token.

#download plugins
1.SonarQube Scanner for Jenkins 
2.Eclipse Temurin installer Plugin 
3.Maven Integration plugin 

#system configuration 
configure sonarqube

#tool configuration
JDK installations 
SonarQube Scanner installations 
Maven installations 

git Repo URL ---> Use Train Repository

#Sonar cube Pipeline

pipeline {
    agent any
    tools {
        jdk 'jdk11'  
        maven 'maven3'
    }
    environment {
	SCANNER_HOME=tool 'sonar'
    }
    stages {
        stage('git Checkout') {
            steps {
                git 'useourpipeline'
            }
        }
        stage('compile code') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('code test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Sonar-analysis') {
            steps {
	            withSonarQubeEnv('sonar') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=sonar-qube-analsys \
		     -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=sonar-qube-analsys '''
		        }
            }
        }
    }
}


#Jfrog - Assignment

jfrog : (t2.medium)
URL ---> 

	username: admin
	password: password

#create repo in jfrog

#download plugins
1.Artifactory 
2.Eclipse Temurin installer Plugin 
3.Maven Integration plugin 

#system configuration 
Jfrog

#tool configuration
JDK installations 
SonarQube Scanner installations 
Maven installations 

git Repo URL ---> 

pipeline {
    agent any
    tools {
        jdk "jdk11"
        maven "maven3"
     }
    stages {
        stage('git checkout') {
            steps {
                git 'useourtrainesystem'
            }
        }
      stage('clean and install') {
            steps {
                   sh 'mvn clean install'
            }
        }
        stage('Sonar-analysis') {
            steps {
	            withSonarQubeEnv('sonar') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=sonar-qube-analsys \
		     -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=sonar-qube-analsys '''
		        }
            }
        }
      stage('upload Jfrog artifact') {
            steps {
                      rtServer (
                      id: 'Artifactory',
                      url: 'IPaddress of your repository',
                      username: 'admin',
                      password: 'password',
                      bypassProxy: true,
                    )
                      rtUpload (
                        serverId: 'Artifactory',
                        spec: '''{
                        "files": [
                             {
                        "pattern": "*.war",
                       "target": "libs-snapshot-local"
                  }
               ]
         }''',
       )
      } 
    }
  }
}
