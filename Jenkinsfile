pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker-compose build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying WordPress...'
                sh 'docker-compose up -d'

                echo 'Retrieving WordPress IP address...'
                sh 'docker-compose exec wordpress bash -c "ip route get 8.8.8.8 | awk \'/src/ {print $1}\'" > wordpress-ip.txt'

                echo 'WordPress IP address:'
                sh 'cat wordpress-ip.txt'
            }
        }
    }
}
a
