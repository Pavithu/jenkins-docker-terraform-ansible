pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'maven', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t pavithu/cicd-poc-jenkins-pavi:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u Pavithu -p Pavi@0518"
          sh "docker push pavithu/cicd-poc-jenkins-pavi:$BUILD_NUMBER"
          }
        }
      }
    }
}

