pipeline {
agent any


  stages {
    stage('Unit Test') {
      steps {
        sh 'mvn clean test'
      }
    }  
    stage('Deploy Standalone') {
      steps {
        sh 'mvn deploy -P standalone'
      }
    }
    stage('Deploy ARM') {
     
      steps {
        sh 'mvn deploy -P arm -Darm.target.name=local-4.2.1-ee -Danypoint.username=ssrivastavarh -Danypoint.password=Miraya@123'
      }
    } 
    
  }
}