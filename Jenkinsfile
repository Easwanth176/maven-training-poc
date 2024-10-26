pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Deploy CloudHub') {
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint_platform')
            }
            steps {
                echo 'Deploying Mule project due to the latest code commit...'
                echo 'Deploying to the configured environment...'
                bat 'mvn clean deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW}'
            }
        }
    }
}
