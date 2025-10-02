pipeline{
    agent any
    environment{
        DOCKER_IMAGE = "houssem128/devops-project:latest"
    }
    Stages {
        stage("Checkout"){
            steps{
                git branch:"main" , url:"https://github.com/Houssem123987/devops-project.git"
            }
        }
        stage("build image"){
            steps{
                bat "docker build -t %DOCKER_IMAGE% ."
            }
        }
        stage('Push Dockerhub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials',
                usernameVariable: 'DOCKER_USER',
                passwordVariable: 'DOCKER_PASS')]) {
                    bat 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    bat 'docker push $DOCKER_IMAGE'
        }
    }
}

}

post {
        always {
            echo 'Pipeline terminé'
        }
        success {
            echo 'Pipeline réussi !'
        }
        failure {
            echo 'Pipeline échoué !'
        }
    }
}