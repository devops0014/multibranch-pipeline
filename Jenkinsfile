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
                sh 'docker run -itd --name bank1 -p 6666:80 shaikmustafa/abinay:bank'
            }
        }
    }
}
