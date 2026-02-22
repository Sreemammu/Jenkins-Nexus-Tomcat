pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Sreemammu/Jenkins-Nexus-Tomcat'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(
                    credentialsId: 'tomcat-creds',
                    path: '',
                    url: 'http://<3.111.39.187>:8080')],
                    contextPath: null,
                    war: 'target/*.war'
            }
        }
    }
}
