pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "houssem128/devops-project:latest"
    }
<<<<<<< HEAD

=======
>>>>>>> 411932d (3eme commit)
    stages {
        stage("Checkout") {
            steps {
                git branch: "main", url: "https://github.com/Houssem123987/devops-project.git"
            }
        }

<<<<<<< HEAD
        stage("Build Image") {
            steps {
                bat "docker build -t $DOCKER_IMAGE ."
=======
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat 'sonar-scanner'
                }
            }
        }

        stage("Build Docker Image") {
            steps {
                bat "docker build -t %DOCKER_IMAGE% ."
>>>>>>> 411932d (3eme commit)
            }
        }

        stage('Push Dockerhub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
<<<<<<< HEAD
                    bat 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    bat 'docker push $DOCKER_IMAGE'
=======
                    bat 'echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
                    bat 'docker push %DOCKER_IMAGE%'
>>>>>>> 411932d (3eme commit)
                }
            }
        }
    }

    post {
<<<<<<< HEAD
        always {
            echo 'Pipeline terminé'
        }
=======
>>>>>>> 411932d (3eme commit)
        success {
            echo 'Pipeline réussi !'
        }
        failure {
            echo 'Pipeline échoué !'
        }
    }
}
