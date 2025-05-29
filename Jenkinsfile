

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Majeed09/jenkins-ci-test.git'
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Jenkins Build: ${currentBuild.fullDisplayName} - ${currentBuild.currentResult}",
                body: """
                    Build URL: ${env.BUILD_URL}

                    Status: ${currentBuild.currentResult}

                    Check the Jenkins console log for details.
                """,
                to: 'majeedm2019@gmail.com',
                attachLog: true
            )
        }
    }
}
















//  stage('Install Dependencies') {
        //    steps {
          //      bat 'npm install'
            //}
        //}

       









