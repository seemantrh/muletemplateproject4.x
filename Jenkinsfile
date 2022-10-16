pipeline {
agent any
   

   tools { 
        maven 'maven' 
        jdk '1.8.0_321' 
    }


  stages {

stage('Deploy ARM') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials') 
      }
      steps {
        sh 'mvn deploy -P arm -Darm.target.name=mule-default4.3-dev3 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR}  -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW}' 
      }
    }
    
  }
}

