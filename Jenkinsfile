pipeline {
    agent {label 'group1'}

    stages {
        stage('checkout') {
            steps {
                git branch: 'main', credentialsId: '8fcbf9a3-9d13-41c1-aaec-ae946e5a61d4', url: 'https://github.com/harendra37/practice.git'
            }
        }
        stage('mvn-build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Deploy-Tomcat') {
            steps {
                sshagent(['18.224.30.52']) {
            sh "scp -o StrictHostKeyChecking=no target/*.war hari@18.224.30.52:/home/hari/apache-tomcat-9.0.58/webapps"
                    
                }
            }
        }
    }
    
}
