pipeline {

  agent any
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean %M2SETTINGS% -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          bat "mvn test"
      }
    }

     stage('Deploy Development') {
      
      steps {
            bat 'mvn -U -V -e -B %M2SETTINGS% -DskipTests -Pdev deploy -DmuleDeploy'
      }
    }
  }
}