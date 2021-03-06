pipeline {
    agent any 
    environment {
        USER= "rafael"
    }
    stages {
        stage('Set Enviroment') { 
            steps {
                sh "virtualenv -p python3 venv && . venv/bin/activate"
                sh "pip3 install -r requirements.txt"
            }
        }
        stage('Test Project') { 
            steps {
                sh ". venv/bin/activate"
                sh "python3 -m pytest -s -v"
            }
        }
        stage('Deploy') {
            when { branch "master" }
            steps {
                sh "cd /home/${env.USER} && sudo mkdir -p projectJenkins"
                sh "sudo cp -r * /home/${env.USER}/projectJenkins"
                sh "sudo rm -r *"
                sh "cd /home/${env.USER}/projectJenkins && . venv/bin/activate && sudo python3 start.py"
            }
        }
    }
}