pipeline {
    agent {
        label 'Jenkins-Agent' // Ensure that this label matches your agent configuration
    }

    tools {
        jdk 'Java17' // Ensure Java17 is correctly configured in Jenkins
        maven 'Maven3' // Ensure Maven3 is correctly configured in Jenkins
    }

    stages {
        stage("CleanUp Workspace") {
            steps {
                cleanWs() // Clean workspace before starting the pipeline
            }
        }

        stage("Checkout from SCM") {
            steps {
                // Make sure credentialsId is correctly configured in Jenkins for GitHub
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/MohammedSamerr/register_app.git'
            }
        }

        stage("Build App") {
            steps {
                // Build the project using Maven
                sh "mvn clean package"
            }
        }

        stage("Test App") {
            steps {
                // Run tests using Maven
                sh "mvn test"
            }
        }
    }
}
