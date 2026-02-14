pipeline {
    agent any

    tools {
        jdk 'jdk21'
    }

    environment {
        ANDROID_HOME = "/home/ubuntu/android-sdk"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/athulkaratte/Taxi-Booking-Android-App.git'
            }
        }

        stage('Grant Permission') {
            steps {
                sh 'chmod +x gradlew'
            }
        }

        stage('Verify Java Version') {
            steps {
                sh 'java -version'
            }
        }

        stage('Clean') {
            steps {
                sh './gradlew clean'
            }
        }

        stage('Build Debug APK') {
            steps {
                sh './gradlew assembleDebug'
            }
        }

        stage('Archive APK') {
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/apk/debug/*.apk',
                                 fingerprint: true
            }
        }
    }
}
