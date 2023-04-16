pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat_ID', path: '', url: 'http://3.144.7.2:8080/')], contextPath: 'webapp', war: '**/*.war'
            }
        }
    }
}
