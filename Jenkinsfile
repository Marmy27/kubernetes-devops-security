pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }
      stage('Unit Test') {
            steps {
              sh "mvn test"
            }
            post {
              always {
             // junit 'target/surefire-report/*.xml'
              jacoco execPattern: 'target/jacoco.exec'
            }
            }
      }   
    }
}