pipeline {
    agent any

    tools {
        nodejs "node"   // make sure node is configured in Jenkins
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/chiranjit04/ionic.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to S3') {
            steps {
                sh '''
                aws s3 sync www/ s3://cj-jenkin-angular/ --delete
                '''
            }
        }
    }
}
