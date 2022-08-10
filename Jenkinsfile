pipeline{

    agent any

    environment {
        DOCKERHUB_CREDENTIALS=credentials('rawabi-dockerhub')
    }

    stages {

        stage('Build') {

            steps {
                sh 'docker build -t rawabim/runaway:latest .'
            }
        }

        stage('Login') {

            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push') {

            steps {
                sh 'docker push rawabim/runaway:latest'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }

}