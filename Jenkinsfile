pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-tf-serving-container') // Ganti 'my-tf-serving-container' sesuai dengan nama yang Anda inginkan
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://docker.io', 'docker-credentials-id') {
                        docker.image('my-tf-serving-container').push('latest') // Ganti 'my-tf-serving-container' sesuai dengan nama yang Anda gunakan sebelumnya
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8501:8501 my-tf-serving-container' // Sesuaikan port dan nama kontainer jika diperlukan
            }
        }
    }
}

