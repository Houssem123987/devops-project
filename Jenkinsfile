pipeline {
    agent any
    environment {
        REPO_URL = 'https://github.com/Houssem123987/devops-project.git'
        BRANCH = 'main'
    }
    stages {
        stage('Prepare Workspace') {
            steps {
                script {
                    // 1️⃣ Supprime complètement le workspace pour repartir propre
                    deleteDir()
                    
                    // 2️⃣ Clone le repo directement dans le workspace Jenkins
                    sh "git clone ${REPO_URL} ."
                    
                    // 3️⃣ Passe à la branche désirée
                    sh "git checkout ${BRANCH}"
                    
                    // 4️⃣ Vérifie que Git fonctionne
                    sh "git status"
                }
            }
        }

        stage("Build Docker Image") {
            steps {
                bat "docker build -t %DOCKER_IMAGE% ."
            }
        }

        stage('Push Dockerhub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    bat 'echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
                    bat 'docker push %DOCKER_IMAGE%'
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
