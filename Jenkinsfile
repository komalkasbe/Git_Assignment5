pipeline {
    agent any

    triggers {
        githubPush()
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test Deploy') {
            agent { label 'test-node' }
            steps {
                echo "Copying files to TEST node..."
                sh 'cp -r * D:/Komal/intellipaat/Assignment/DevOps/Jenkins/Jenkins/TestServer/'
            }
        }

        stage('Prod Deploy') {
            agent { label 'prod-node' }
            steps {
                echo "Copying files to PROD node..."
                sh 'cp -r * D:/Komal/intellipaat/Assignment/DevOps/Jenkins/Jenkins/ProdServer/'
            }
        }
    }

    post {
	success {
            echo "Build succeeded!"
        }
        failure {
            echo "Build failed. Not deploying to prod."
        }
    }
}
