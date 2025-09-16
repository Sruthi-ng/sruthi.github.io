pipeline {
    agent any

    // Optional: Define environment variables for the pipeline.
    environment {
        // Example: a variable to hold the build version
        BUILD_VERSION = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build') {
            steps {
                // Example for a Node.js project:
                echo 'Building the project...'
                // sh 'npm install'
                // sh 'npm run build'
                //
                // Example for a Maven (Java) project:
                // sh 'mvn clean install'
                echo 'Build complete!'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests, integration tests, etc.
                echo 'Running tests...'
                // sh 'npm test'
                // sh 'mvn test'
                echo 'All tests passed!'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Store the build output (e.g., a compressed file or executable)
                echo 'Archiving build artifacts...'
                // This command archives files so you can download them from the Jenkins UI
                // archiveArtifacts artifacts: 'build/dist/**/*', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                // Deploy to a staging or production environment.
                echo "Deploying version ${env.BUILD_VERSION}..."
                // Example: Use a shell script to deploy
                // sh './deploy-to-server.sh'
                echo 'Deployment successful!'
            }
        }
    }
}
