pipeline {
    agent any
    tools {
        maven "Maven-3.6.3"
        jdk "jdk8"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                bat 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                script {
                    docker.withRegistry('localhost:5000') {
                      docker.build("localhost:5000/spring-boot-demo:${env.BUILD_TAG}").push()
                    }
                }
            }
        }
    }
}