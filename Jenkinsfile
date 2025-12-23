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
        stage ("Push") {
            steps {
                sh 'docker push naveenk96/mbranch:bank'
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 shaikmustafa/abinay:bank'
            }
        }
    }
}
