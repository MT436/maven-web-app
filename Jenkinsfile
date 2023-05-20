pipeline {
    agent any
    stages{
        stage('build: maven'){
            steps{
                sh 'mvn clean package' 
            }
        }
        stage('deploy: tomcat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://172.31.18.18:8085/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}