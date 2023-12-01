pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'maven:3-alpine'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('docker-build') {
                agent any
                steps {
                    sh '''cd /var/jenkins_home/workspace/simple-java-maven-app1/target
                    cp ../Dockerfile ./
                    docker build -t testproject .'''
                }
            }
    }
}