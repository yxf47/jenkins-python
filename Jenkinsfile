pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/username/repo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run Script') {
            steps {
                sh 'python helloworld.py'
            }
        }
    }
}
