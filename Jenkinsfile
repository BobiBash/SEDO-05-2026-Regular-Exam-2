pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Restore') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --configuration Release --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test --configuration Release --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }

        success {
            echo 'Build and tests passed.'
        }

        failure {
            echo 'Build or tests failed.'
        }
    }
}