pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 sahithi0622/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhubcreds') {
                        sh 'docker push sahithi0622/paytm:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 shaikmustafa/paytm:bank'
            }
        }
    }
}
