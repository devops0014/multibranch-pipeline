pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t shaikmustafa/abinay:bank .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push shaikmustafa/abinay:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 shaikmustafa/abinay:bank'
            }
        }
    }
}
