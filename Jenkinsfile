pipeline {
    agent any
    
    tools {
        jdk 'JDK-21'
        maven 'Maven-3.9'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/celmarka/student-api.git', branch: 'main'
            }
        }
        
        stage('Build & Test') {
            steps {
                sh 'mvn clean verify'
            }
        }
        
        stage('Publish Test Report') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline terminée'
        }
        success {
            echo '✅ Pipeline réussie !'
        }
        failure {
            echo '❌ Pipeline échouée -- consultez les logs.'
        }
    }
}