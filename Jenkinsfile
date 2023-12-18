pipeline {
    agent { label 'ansible' }
    environment {
        PATH = "/usr/local/bin:/usr/bin:/home/jenkins/.local/bin:/usr/lib64/python3.11/site-packages:/usr/bin/python3.11"
    }
    
    stages {
        stage('Git checkout') {
           steps {    
                git url: 'https://github.com/sda1891/vector_role.git', branch: 'main'
           }
        }
        stage('Install requirements') {
            steps {
                sh 'ansible-galaxy install -r requirements.yml'
            }
        }
        stage('Run molecule') {
            steps {
                sh 'molecule test -s centos8'
            }
        }
        stage('Clean role') {
            steps {
                sh 'ansible-galaxy role remove vector-role'
            }
        }
    }
}
