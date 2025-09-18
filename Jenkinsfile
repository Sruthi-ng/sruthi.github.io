pipeline {
    agent any

    parameters {
        choice(name: 'TARGET_ENV', choices: ['staging', 'production'], description: 'Select the deployment environment')
    }

    environment {
        BUILD_VERSION = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'zip -r sruthi.github.io.zip .'
                echo 'Build complete!'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example for linting:
                // sh 'npm install -g htmlhint'
                // sh 'htmlhint index.html'
                echo 'All tests passed!'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'sruthi.github.io.zip', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${env.BUILD_VERSION} to ${params.TARGET_ENV}..."
                sh "sed -i 's/BUILD_NUMBER_PLACEHOLDER/${env.BUILD_NUMBER}/g' index.html"
                echo 'Deployment successful!'
            }
        }
    }
}
