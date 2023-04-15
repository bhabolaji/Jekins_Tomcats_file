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
             deploy adapters: [tomcat9(credentialsId: 'tomcat_id', path: '', url: 'http://18.119.116.79:8080/')], contextPath: 'webapp', war: '**/*.war'
            }
        }
    }
}
