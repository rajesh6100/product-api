pipeline {

  agent any
  
  environment {
    ANYPOINT_PLATFORM_CREDENTIALS = credentials('4269897c-b00e-4235-aa38-a1c48c468987')
  }
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean %M2SETTINGS% -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          echo "***** MUnit test cases execution *****"
      }
    }

     stage('Deploy Development') {
     
      environment {
    CLIENT_ID = credentials('DEV_CLIENT_ID')
    CLIENT_SECRET = credentials('DEV_CLIENT_SECRET')
      }
      steps {
            bat 'mvn -U -V -e -B %M2SETTINGS% -DskipTests -Pdev deploy -DmuleDeploy -Danypoint.username="%ANYPOINT_PLATFORM_CREDENTIALS_USR%" -Danypoint.password="%ANYPOINT_PLATFORM_CREDENTIALS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%"'
      }
    }
  }
}