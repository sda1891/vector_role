pipeline {
    agent { label 'ansible' }
    stages {
        stage('Git checkout') {
           steps {    
                git url: 'https://github.com/sda1891/vector_role.git', branch: 'main'
           }
        }
        stage('Install requirements') {
            steps {
                sh 'PATH=$PATH:/home/jenkins/.local/bin ansible-galaxy install -r requirements.yml'
            }
        }
        stage('Run molecule') {
            steps {
                sh 'PATH=$PATH:/home/jenkins/.local/bin molecule test -s centos8'
            }
        }
        stage('Clean role') {
            steps {
                sh 'PATH=$PATH:/home/jenkins/.local/bin ansible-galaxy role remove vector-role'
            }
        }
    }
}
