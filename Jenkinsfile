pipeline {
    agent any
    stages {
        stage('Install Pip') {
            steps {
                script {
                    // Check if pip is installed
                    def pipInstalled = sh(script: 'command -v pip3', returnStatus: true) == 0
                    if (!pipInstalled) {
                        // Install pip
                        sh 'curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py'
                        sh 'python3 get-pip.py --user'
                        // Add pip to PATH
                        sh 'echo "export PATH=$HOME/.local/bin:$PATH" >> ~/.bashrc'
                        sh 'source ~/.bashrc'
                    }
                }
            }
        }
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/yxf47/jenkins-python.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('Run Script') {
            steps {
                sh 'python3 helloworld.py'
            }
        }
    }
}
