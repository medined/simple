def mvnCmd = "mvn"

pipeline {
  agent {
    label 'maven'
  }
  stages {
    stage('Build App') {
      steps {
        sh "${mvnCmd} install -DskipTests=true"
      }
    }
    stage('Test') {
      steps {
        sh "${mvnCmd} verify"
        step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
      }
    }
  }
}
