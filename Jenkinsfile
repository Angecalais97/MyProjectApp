pipeline {
  agent any
  tools {
    maven 'maven3'
  } 
  environment {
    SONARQUBE_SCANNER_HOME = tool 'SonarQube-Scanner'
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
          sh """
            ${SONARQUBE_SCANNER_HOME}/bin/sonar-scanner \
            -Dsonar.projectKey=MyProjectApp \
            -Dsonar.host.url=http://3.80.110.90:9000 \
            -Dsonar.token=sonar-token \
            -X
          """
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
