pipeline {
    agent any
    tools {
        maven 'Maven3.8.1'
    }
    
    stages {
        stage('gitcheckout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Srikanth19594/sparkjava-war-example.git']]])
            }
        }
        stage('build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-login', path: '', url: 'http://54.89.171.51:8090/')], contextPath: 'sparkjava-war-example', war: '**/*.war'
            }
        }
    }
}
