pipeline {
    agent any

    tools {
        gradle 'Gradle'  // Jenkins-installed Gradle (configure this in Jenkins global tools)
        jdk 'JDK'        // Jenkins-installed JDK
    }

    stages {
        stage('Checkout') {
            steps {
                echo '🔄 Cloning GitHub repository...'
                git branch: 'master', url: 'https://github.com/ShashiMadari/Maventogradle.git'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Building the project...'
                sh './gradlew build'
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
