pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t bus .'
            }
        }
        stage('Tag') {
            steps {
               sh 'docker tag bus naveenk96/mbranch:bus'
            }
        }
        stage ("Push") {
              steps {
                script {
                withDockerRegistry(credentialsId: 'docker') {
                    sh 'docker push naveenk96/mbranch:bus'
                }
            }
          }
        }     
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name buscont -p 8888:80 naveenk96/mbranch:bus'
            }
        }
    }
}
