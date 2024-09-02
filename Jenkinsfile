pipeline {
    agent any

    parameters {
        string(name: 'data_dir', defaultValue: '/srv/personas-bots/data', description: 'Directory where app data are stored (config and personas descriptions)')
    }

    environment {
        DATA_DIR = "${params.data_dir}"
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Test') {
            steps {
                sh 'docker compose run personas-bots npm run check-types'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}