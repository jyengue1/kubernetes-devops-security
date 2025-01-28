pipeline {
  agent any

  stages {
      stage('Build an Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }   
      stage('Unit Tests - JUnit and Jacoco') {
            steps {
              sh "mvn test"
            }
            post {
              always {
                junit 'target/surefire-reports/*.xml'
                jacoco execPattern: 'target/jacoco.exec'
              }
            }
        }
      stage('Docker Build and Push') {
            steps {
              sh 'docker build -t jyengue1/numeric-app:""$GIT_COMMIT"" .'
              archive 'docker push jyengue1/numeric-app:""$GIT_COMMIT""'
            }
      }
    }
}