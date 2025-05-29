pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t reddy0314/abinay:train .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dock-pass') {
                        sh 'docker push reddy0314/abinay:train'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 reddy0314/abinay:train'
            }
        }
    }
}
