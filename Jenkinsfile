pipeline {
    agent any

    environment {
        PROJECT_NAME = "carwebsite"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/karthickbalaraman6/carwebsite.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh 'echo "Listing project files..."'
                sh 'ls -ltr'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build Completed Successfully for Static Website"'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.html, **/*.css, **/*.js', fingerprint: true
            }
        }

        stage('Deploy to Apache') {
    steps {
        sh '''
        echo "Deploying to Apache..."
        cp -r * /var/www/html/
        '''
    }
}
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
