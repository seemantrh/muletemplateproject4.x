pipeline {
agent any

environment {
        ANYPOINT = credentials('ANYPOINT_PLATFORM_CREDENTIALS')
        MULE_SETTINGS = '/opt/maven/settings/np-settings.xml'
        MVN = 'mvn'
        GIT = 'git'
        ANYPOINT_CREDENTIALS_USR=ssrivastavarh	
        ANYPOINT_CREDENTIALS_PSW=Miraya@123
        
}
    
    
tools {
  maven 'Maven-3.5.2'
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
        sh 'mvn deploy -P arm -Darm.target.name=local-3.9.0-ee -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW}'
      }
    } 
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      
      steps {
        sh 'mvn deploy -P cloudhub -Dmule.version=3.9.0 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW}'
      }
    }
  }
}