pipeline {
    agent any 
    environment {
        GIT_REPO = "https://github.com/rarafa245/jenkins_test"
        USER= "rafael"
    }
    stages {
        stage('Clone Repo') { 
            steps {
                sh "virtualenv -p python3 venv && . venv/bin/activate"
                sh "pip3 install -r requirements.txt"
            }
        }
        stage('Test') { 
            steps {
                sh ". venv/bin/activate"
                sh "python3 -m pytest -s -v"
            }
        }
        stage('Deploy') {
            steps {
                sh "cd /home/${env.USER} && sudo mkdir projectJenkins"
                sh "sudo mv * /home/${env.USER}/projectJenkins"
                sh "cd /home/${env.USER}/projectJenkins && . venv/bin/activate && sudo python3 start.py"
            }
        }
    }
}