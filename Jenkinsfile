pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                echo 'cloning the repo'
                git url: 'https://github.com/manager-dot/Devops.git' , branch: 'main'
            }
        }
        stage('Install Dependency') {
            steps {
                echo 'installing dependency'
                sh 'npm install'
            }
        }
        stage('Run tests') {
            steps {
                echo 'running unit test '
                sh 'npm test'
            }
        }
        stage('build artifacts') {
            steps {
             
              sh  'mkdir -p assesmenttoday  && echo "This is a test file" > assesmenttoday/readme.txt && zip -r build.zip assesmenttoday'
                 
            }
        }
        stage('Archive artifact') {
            steps {
             archiveArtifacts 'build.zip'
                 
            }
        }
       
        stage('cleaning up workspace ') {
            steps {
            echo 'cleaning up workspace...'
            sh 'rm -rf assesmenttoday build.zip'
                 
            }
        }
       
        stage('Notify ') {
            steps {
            echo 'build complete'
                 
            }
        }
       
    }
}

