pipeline {
    agent any

    environment {
        ANDROID_HOME = "/home/ubuntu/android-sdk"
        GRADLE_USER_HOME = "/home/jenkins/.gradle"
    }

    tools {
        jdk 'jdk17'
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Cloning Repository..."
                git branch: 'main',
                    url: 'https://github.com/athulkaratte/Taxi-Booking-Android-App.git'
            }
        }

        stage('Grant Execute Permission') {
            steps {
                sh 'chmod +x gradlew'
            }
        }

        stage('Clean Project') {
            steps {
                sh './gradlew clean'
            }
        }

        stage('Build Debug APK') {
            steps {
                sh './gradlew assembleDebug'
            }
        }

        stage('Verify APK') {
            steps {
                sh 'ls -la app/build/outputs/apk/debug/'
            }
        }

        stage('Archive APK') {
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/apk/debug/*.apk',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build Successful ✅'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}
