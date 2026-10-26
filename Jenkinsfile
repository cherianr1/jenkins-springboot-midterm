
pipeline {
    agent any

    tools {
        maven 'Maven-HW7'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Fat JAR') {
            steps {
                sh 'mvn -B clean package'
            }
        }

        stage('Verify Fat JAR') {
            steps {
                sh '''
                    ls -lh target/*.jar
                    jar tf target/jenkins-springboot-midterm-*.jar | grep 'BOOT-INF/'
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar',
                                 fingerprint: true
            }
        }
    }
}
