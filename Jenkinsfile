pipeline {
  agent {label 'java'}
  stages{
    stage('checkout') {
      steps {
        sh 'rm -rf Parcel-service'
        sh 'git clone https://github.com/tarundanda147/Parcel-service.git'
   }
}
 stage('build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
              }
 }Jenkinsfile

pipeline { agent any

environment {
    MAVEN_HOME = tool 'Maven'
}

stages {
    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Build') {
        steps {
            script {
                sh "${MAVEN_HOME}/bin/mvn clean package"
            }
        }
    }

    stage('Run Locally') {
        steps {
            script {
                // Run the Spring Boot application locally
                sh "java -jar target/myhealthapp.jar &"
                // Sleep for a while to allow the application to start (adjust as needed)
                sleep 30
            }
        }
    }

    stage('Deploy to Tomcat') {
        steps {
            script {
                // Copy the JAR file to the Tomcat webapps directory
                sh "cp target/weather-forecast-app-1.0-SNAPSHOT.jar /path/to/tomcat/webapps/"

                // Restart Tomcat
                sh "/path/to/tomcat/bin/shutdown.sh"
                sh "/path/to/tomcat/bin/startup.sh"
            }
        }
      stage('Run Locally') {
        steps {
                sh "java -jar simple-parcel-service-app-1.0-SNAPSHOT.jar &"
                sh 'sleep 30'
            }
        }
    stage
    stage('deploy') {
            steps {
              sh 'ssh root@172.31.9.118'
              sh 'scp -r /home/slave4/workspace/pipelineparcel/target/simple-parcel-service-app-1.0-SNAPSHOT.jar root@172.31.9.118:/opt/apache-tomcat-9.0.85/webapps'
            }
        }
    }
}
