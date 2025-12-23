pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t train .'
            }
        }
        stage('Tag') {
            steps {
               sh 'docker tag bank naveenk96/mbranch:train'
            }
        }
        stage ("Push") {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker') {
                    sh 'docker push naveenk96/mbranch:train'
                }
            }
           }
        }  
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 naveenk96/mbranch:train'
            }
        }
    }
}
