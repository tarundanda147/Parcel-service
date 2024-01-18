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
    stage('deploy') {
            steps {
              sh 'scp -r /home/slave4/workspace/parcelservice_feature-2/target/* root@172.31.9.118:/opt/apache-tomcat-9.0.85/webapps'
            }
        }
    }
}

