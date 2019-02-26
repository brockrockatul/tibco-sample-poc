pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /C/Users/brock/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                dir('tibco.sample.ems.poc.application.parent'){
                    sh 'mvn -DskipTests clean package' 
                }
                
            }
        }
    }
    stage ('Build docker image') { 
        agent {
            docker {
                image 'maven:latest'
                args '-v /root/.m2:/root/.m2 -v /var/run/docker.sock:/var/run/docker.sock'
            }
        }
        steps {
            sh 'mvn -Ddocker.skip=false -Ddocker.host=unix:///var/run/docker.sock docker:build'
        }
    }
}
