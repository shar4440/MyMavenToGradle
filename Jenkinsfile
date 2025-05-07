pipeline {
    agent any

    tools {
        gradle 'Gradle'  // Name of Gradle installed in Jenkins
        jdk 'JDK'        // Name of JDK installed in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo '🔄 Cloning GitHub repository...'
                git branch: 'master', url: 'https://github.com/shar4440/MyMavenToGradle.git'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Building the project using Gradle wrapper...'
                sh './gradlew clean build'
            }
        }

        stage('Run Jar') {
            steps {
                echo '🚀 Running the generated JAR...'
                sh 'java -jar build/libs/MyMavenToGradle-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully.'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
