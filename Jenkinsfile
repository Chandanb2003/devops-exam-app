pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "chandan669/devopsexamapp:latest"
    }

    stages {
        stage('Git Checkout') {
            steps {
                git url: 'https://github.com/Chandanb2003/devops-exam-app.git', 
                    branch: 'master'
            }
        }

        stage('Verify Docker Compose') {
            steps {
                sh '''
                docker compose version || { echo "Docker Compose not available"; exit 1; }
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('backend') {
                    script {
                        withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                            sh "docker build -t ${DOCKER_IMAGE} ."
                            sh "docker push ${DOCKER_IMAGE}"
                        }
                    }
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                sh '''
                docker compose down --remove-orphans || true
                docker compose up -d --build

                echo "Waiting for MySQL to be ready..."
                timeout 120s bash -c '
                while ! docker compose exec -T mysql mysqladmin ping -uroot -prootpass --silent;
                do 
                    sleep 5;
                    docker compose logs mysql --tail=5 || true;
                done'

                sleep 10
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                echo "=== Container Status ==="
                docker compose ps -a
                echo "=== Testing Flask Endpoint ==="
                curl -I http://localhost:5000 || true
                '''
            }
        }
    }

    post {
        success {
            node {
                echo '🚀 Deployment successful!'
                sh 'docker compose ps'
                archiveArtifacts artifacts: 'trivy-fs-report.html', allowEmptyArchive: true
            }
        }
        failure {
            node {
                echo '❗ Pipeline failed. Check logs above.'
                sh '''
                echo "=== Error Investigation ==="
                docker compose logs --tail=50 || true
                '''
            }
        }
        always {
            node {
                sh '''
                echo "=== Final Logs ==="
                docker compose logs --tail=20 || true
                '''
                archiveArtifacts artifacts: 'trivy-fs-report.html', allowEmptyArchive: true
            }
        }
    }
}
