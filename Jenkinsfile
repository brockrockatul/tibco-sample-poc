pipeline {
    agent {
        docker {
            image 'maven-alpine:3.6' 
            args '-v /root/.m2:/root/.m2' 
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
}
