
pipeline {
    agent any

    stages {
        stage('Cloning git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/IsaqueGarcia/jk-public-gh.git'
            }
        }
        stage('Build image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Deploy application') {
            steps {
                sh '''
                # docker stop webapp-ctr
                docker run --rm -d -p 3000:3000 --name webapp-ctr webapp:${BUILD_NUMBER}
                '''
            }
        }
    }
}
