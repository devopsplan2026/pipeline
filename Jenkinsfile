pipeline { 
    agent { label 'red' }

environment {
    DEPLOY_DIR = "/opt/myflaskapp"
}

stages {
    stage('Checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/devopsplan2026/pipeline.git'
        }
    }

    stage('Deploy') {
        steps {
            sh '''
                sudo cp app.py ${DEPLOY_DIR}/
                sudo systemctl restart myflaskapp
            '''
        }
    }
}

post {
    success {
        echo 'Deployment successfully!'
    }
    failure {
        echo 'Deployment failed.'
    }
}
}