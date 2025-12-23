pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t bank .'
            }
        }
        stage('Tag') {
            steps {
               sh 'docker tag bank naveenk96/mbranch:bank'
            }
        }
         steps {
                script {
                withDockerRegistry(credentialsId: 'docker') {
                    sh 'docker push naveenk96/mbranch:bank'
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bankcont -p 4455:80 naveenk96/mbranch:bank'
            }
        }
    }
}
