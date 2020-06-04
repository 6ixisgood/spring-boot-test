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
                bat 'docker build --rm -t abcollins31/spring-boot-demo .'
                bat 'docker tag abcollins31/spring-boot-demo myhost:8081/demo/spring-boot-demo'
            }
        }
    }
}