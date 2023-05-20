pipeline {
    agent any
    parameters {
      string defaultValue: '0', name: 'start/n stop', trim: true
      }

    stages{
        stage('UnitTest: maven'){
            steps{
                sh 'mvn test' 
            }
        }
        stage('Integration test: maven'){
            steps{
                sh 'mvn verify -DskipUnitTest' 
            }
        }
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
