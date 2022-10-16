pipeline {
agent any
   

   tools { 
        maven 'maven' 
        jdk '1.8.0_321' 
    }


  stages {


 
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