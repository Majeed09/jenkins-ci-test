pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Majeed09/jenkins-ci-test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    def testStatus = bat(script: 'npm test', returnStatus: true)
                    if (testStatus != 0) {
                        currentBuild.result = 'FAILURE'
                    }
                    emailext (
                        subject: "Test Stage Result: ${currentBuild.currentResult}",
                        body: "The test stage has completed with status: ${currentBuild.currentResult}.",
                        to: 'YOUR_EMAIL_HERE',
                        attachLog: true
                    )
                }
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                script {
                    def auditStatus = bat(script: 'npm audit', returnStatus: true)
                    if (auditStatus != 0) {
                        currentBuild.result = 'FAILURE'
                    }
                    emailext (
                        subject: "Security Scan Result: ${currentBuild.currentResult}",
                        body: "The security scan stage has completed with status: ${currentBuild.currentResult}.",
                        to: 'YOUR_EMAIL_HERE',
                        attachLog: true
                    )
                }
            }
        }
    }
}








