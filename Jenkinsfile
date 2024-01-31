pipeline {
    agent any 
    tools {
         maven 'maven'
         jdk 'java'
    }
    stages {
        stage('Stage-0 : Static code analysis using Sonarqube') { 
            steps {
                sh 'mvn sonar:sonar'
            }
        }
        stage('Stage-1 : Clean') { 
            steps {
                sh 'mvn clean'
            }
        }
         stage('Stage-2 : Validate') { 
            steps {
                sh 'mvn validate'
            }
        }
         stage('Stage-3 : Compile') { 
            steps {
                sh 'mvn compile'
            }
        }
         stage('Stage-4 : Test') { 
            steps {
                sh 'mvn test'
            }
        }
        stage('Stage-5 : package') { 
            steps {
                sh 'mvn package'
            }
        }
        stage('Stage-6 : verify') { 
            steps {
                sh 'mvn verify'
            }
        }
        stage('Stage-7 : install') { 
            steps {
                sh 'mvn install'
            }
        }
        stage('Stage-8 : Deploy an Artifact to Artifactory manager i.e Nexus/JFrog') { 
            steps {
                sh 'mvn deploy'
            }
        }
        stage('Stage-9 : Deployment- Deploy an Artifact cloudbinary-2.0.0-release.war file to Tomcat server') { 
            steps {
                sh 'curl -u admin:redhat@123 -T target/**.war "http://54.236.18.91:8080/manager/text/deploy?path=/cbapps&update=true"'
            }
        }
        stage('Stage-10 : smoketest') { 
            steps {
                sh 'mvn curl --retry-delay 10 --retry 5 "http://54.236.18.91:8080/cbapps"'
            }
        }
    }
}