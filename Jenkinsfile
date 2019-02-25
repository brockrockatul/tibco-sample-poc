pipeline {
    agent {
        docker {
            image 'maven' 
            args '-v C:/Users/brock/.m2:/root/.m2' 
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
