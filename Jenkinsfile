pipeline {
  agent {label 'java'}
  stages{
    stage('checkout') {
      steps {
        sh 'rm -rf simple-parcel-service-app'
        sh 'git clone https://github.com/tarundanda147/Parcel-service.git'
   }
}
 stage('build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
   
            }
        }
    }
}
