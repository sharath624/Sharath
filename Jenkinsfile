pipeline {
    agent any  // or 'label("build-node")' to run on specific slave
    tools {
        maven 'Maven 3.8.7' // Name of Maven installation in Jenkins Global Tools
        jdk 'Java 11'        // Name of JDK installation in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-repo>.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build and archive successful!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
