pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t shaikmustafa/abinay:bus'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push shaikmustafa/abinay:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank -p 9999:80 shaikmustafa/abinay:bus'
            }
        }
    }
}
