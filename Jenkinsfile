pipeline {
    agent any 
    stages {
        stage('Clone Repo') { 
            steps {
                echo "Cloning..."
            }
        }
        stage('Test') { 
            steps {
                sh "python3 -m pytest -s -v"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying"
            }
        }
    }
}