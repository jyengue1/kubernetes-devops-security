pipeline {
  agent any

  stages {
      stage('Build an Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }   
    }
}