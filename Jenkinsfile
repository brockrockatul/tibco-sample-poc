pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /C/Users/brock/.m2:/root/.m2' 
        }
    }
    stages {
        stage ('Build and Package') { 
            steps {
                 dir('tibco.sample.ems.poc.application.parent'){
                     sh 'mvn -DskipTests clean package initialize docker:build'
                 }
               
            }
        }
        stage ('Build docker image') { 
            agent any
            steps {
                script {
                     withDockerServer([uri: 'unix\:///var/run/docker.sock']) {
                            def myImage = docker.image('tibco/sapmle-ems')
                            myImage.pull()
                         //myImage.tag("brockrockatul/tibco-sapmle-ems:${BUILD_NUMBER}")
                           
                        
                     }
                }         
            }
        }
        
    }
    
}
