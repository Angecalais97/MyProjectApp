pipeline {
  agent any
 'maven3' tools {
    maven 
  } 
  environment {
    SONARQUBE_SCANNER_HOME = tool 'SonarQubeScanner'
  }
  stages {
    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('SonarQube analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh "${SONARQUBE_SCANNER_HOME}/bin/sonar-scanner"
        }
      }
    }
    // stage('Quality Gate') {
    //   steps {
    //     timeout(time: 1, unit: 'HOURS') {
    //       waitForQualityGate abortPipeline: true
    //     }
    //   }
    // }
  }
}
