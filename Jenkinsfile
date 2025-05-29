pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t reddy0314/abinay:bank .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dock-pass') {
                        sh 'docker push reddy0314/abinay:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 reddy0314/abinay:bank'
            }
        }
    }
}
