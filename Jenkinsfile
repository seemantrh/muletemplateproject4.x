pipeline {
agent any
   

   tools { 
        maven 'maven 3.8.5' 
        jdk '1.8.0_321' 
    }


  stages {

   stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }

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