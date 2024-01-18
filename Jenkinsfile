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
 }     
      stage('Run Locally') {
        steps {
                sh "java -jar target/simple-parcel-service-app-1.0-SNAPSHOT.jar &"
                sh 'sleep 10'
            }
        }
    stage('deploy') {
            steps {
              sh 'ssh root@172.31.9.118'
              sh 'scp -r /home/slave4/workspace/pipelineparcel/target/simple-parcel-service-app-1.0-SNAPSHOT.jar root@172.31.9.118:/opt/apache-tomcat-9.0.85/webapps'
              sh "/opt/apache-tomcat-9.0.85/bin/shutdown.sh"
              sh "/opt/apache-tomcat-9.0.85/bin/startup.sh"
              
            }
        }
    }
}
