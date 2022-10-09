pipeline {
agent any


    
tools {
  maven 'Maven-3.8.5'
}
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
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      
      steps {
        sh 'mvn deploy -P cloudhub -Dmule.version=4.2.1 -Danypoint.username=ssrivastavarh -Danypoint.password=Miraya@123'
      }
    }
  }
}