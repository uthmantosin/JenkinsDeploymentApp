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
                deploy adapters: [tomcat9(credentialsId: 'tomcatpassword', path: '', url: 'http://18.207.96.127:8080/')], contextPath: 'myapp', war: '**/*.war'
            }
        }
    }
}
