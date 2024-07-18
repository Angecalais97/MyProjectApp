pipeline{
  agent any
  tool name: 'maven3', type: 'maven'
  stages{
    stage('build'){
      steps{
        script{
          mvn clean package
        }   
        
      }
    }
  }
}
