pipeline{
  agent any
  tool name: 'maven3', type: 'maven'
  stages{
    stage('build'){
      steps{
        script{
          sh 'mvn clean package'
        }   
        
      }
    }
  }
}
