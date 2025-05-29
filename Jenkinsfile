pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t reddy0314/abinay:bus .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dock-pass') {
                        sh 'docker push reddy0314/abinay:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 8888:80 reddy0314/abinay:bus'
            }
        }
    }
}
