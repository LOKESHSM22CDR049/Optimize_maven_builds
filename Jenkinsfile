pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout from Git (replace with your repository)
                git 'https://github.com/yourusername/your-repo.git'
            }
        }
        
        stage('Build') {
            steps {
                // Run Maven Build
                sh 'mvn clean install -Pproduction -T 4'
            }
        }

        stage('Deploy') {
            steps {
                // Execute the jar file (replace the jar name)
                sh 'java -jar target/your-built-file.jar'
            }
        }
    }

    post {
        always {
            echo 'Build and deploy complete'
        }
    }
}
