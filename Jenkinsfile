pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'cd MwtApp && mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'cd MwtApp && mvn test'
            }
        }        
        
        stage('Deploy to Tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcatpassword', path: '', url: 'http://44.202.158.100:8080/')], contextPath: 'mybaby', war: '**/*.war'
            }
        }
    }
}
