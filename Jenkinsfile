pipeline {
    agent any

    tools {
        jdk 'jdk17'
    }

    environment {
        ANDROID_HOME = "/home/ubuntu/android-sdk"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/athulkaratte/Taxi-Booking-Android-App.git'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean assembleDebug --stacktrace'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/apk/debug/*.apk'
            }
        }
    }
}
