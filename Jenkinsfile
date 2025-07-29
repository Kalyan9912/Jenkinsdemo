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
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    . venv/bin/activate
                    python3 -m py_compile app.py
                '''
            }
        }

        stage('Deploy to EC2 with Ansible') {
            steps {
                sh '''
                    . venv/bin/activate
                    ansible-playbook -i ansible/inventory.ini ansible/deploy.yml
                '''
            }
        }
    }
}
