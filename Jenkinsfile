pipeline {
    agent any
    stages {
        stage ('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/dev']], extensions: [], userRemoteConfigs: [[credentialsId: 'be60cc0a-10e3-4404-b228-a9da7efbcdbf', url: 'https://github.com/RICHNVRDIE/new-repo.git']])
                
            }
        }
        stage ('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage ('deploy to tomcat') {
            steps {
               deploy adapters: [tomcat8(credentialsId: 'c2271a8f-7dba-4dc5-98bd-82d4f846ca5e', path: '', url: 'http://20.0.188.64:8080/')], contextPath: null, war: '**/*.war' 
            }
        }
    }
}
