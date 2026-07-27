pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t bsanthosh27/san:train .'
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 bsanthosh27/san:train'
            }
        }
    }
}
