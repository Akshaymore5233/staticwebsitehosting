pipeline {
    agent any

    environment {
        MAVEN_HOME = '/usr/share/maven'
        JAVA_HOME = '/usr/bin/java'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from GitHub
                sh 'echo "cloniing github repo"'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'U7ON2T3WH57MMMMARVQHT5IOLB7ZDXOHFXAUEB3CQRDA66KLDUX3RXPE5E']]])
                sh 'echo "cloniing github repo clonning comlited###############"'
            }
        }

        stage('Build') {
            steps {
                // Set up Maven and Java in the PATH
                script {
                    sh 'echo "chaking maven @@@@@@@@@@@@@@@@"'
                    def mavenHome = tool 'Maven'
                    env.PATH = "${mavenHome}/bin:${env.JAVA_HOME}/bin:${env.PATH}"
                    sh 'echo "maven complited!!!!!!!!!!!!!!!!!!!!!!!!!"'
                }
                // Build the Java application using Maven
                sh 'echo "Build the Java application using Maven"'
                sh 'mvn clean install'
                sh 'echo "Build comlited................"'
            }
        }

        stage('Test') {
            steps {
                // Run tests using Maven
                sh 'mvn test'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the Java application to production (replace with your deployment script)
                sh 'echo "Deploying to production..."'
                // Additional deployment steps can be added here
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed. Taking necessary actions...'
        }

        always {
            echo 'Performing maintenance tasks...'
        }
    }
}
