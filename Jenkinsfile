pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking....'
                git branch: 'main', url: 'https://github.com/Kalyan9912/Jenkinsdemo.git'


            }
        }
        stage('Clone') {
            steps {
                echo 'Cloning project (skipped as this is local)...'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Deploy to EC2 with Ansible') {
            steps {
                sh 'ansible-playbook -i ansible/inventory.ini ansible/deploy.yml'
            }
        }
    }
}   
    
