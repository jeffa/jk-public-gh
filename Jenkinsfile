pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                git 'https://github.com/jeffa/jk-public-gh.git'
            }
        }
        stage('build') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('stop') {
            steps {
                sh 'docker stop webapp_ctr'
            }
        }
        stage('deploy') {
            steps {
                sh 'docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}'
            }
        }
    }
}
