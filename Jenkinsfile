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


	echo deploying to ARM
	local TOKEN_BODY=$(curl --tlsv1.2 -X POST  https://anypoint.mulesoft.com/accounts/login -H 'Content-Type: application/json' -d '{"username": "rhintegrations","password": "RHintegrations@1"}'   )
	echo $TOKEN_BODY
	local ACCESS_TOKEN=`echo $TOKEN_BODY | /usr/local/bin/jq -r '.access_token'`
	local TOKEN_TYPE=`echo $TOKEN_BODY | /usr/local/bin/jq -r '.token_type'`

	local AUTH_HEADER=`echo Authorization: $TOKEN_TYPE $ACCESS_TOKEN`
	echo authorization header "$AUTH_HEADER"
	# Upload Application
	echo Deploying Application with versionId $MMC_APP_VERSION $TARGET_SERVERS

	local MMC_RESULT=$(curl --tlsv1.2 -F file=@$APP_JAR -F artifactName=$APP_NAME-$APP_VERSION  -F targetId=$TARGET_SERVERS -H 'Content-Type: multipart/form-data' -H "$AUTH_HEADER" -H 'X-ANYPNT-ORG-ID:31f7a0ca-9668-41a3-bc2d-ef21488fea66' -H 'X-ANYPNT-ENV-ID:41bd9264-3709-4a0c-a0fb-db5c30291c92' https://anypoint.mulesoft.com/hybrid/api/v1/applications)

	echo $MMC_RESULT

      }
    }
    
  }
}

