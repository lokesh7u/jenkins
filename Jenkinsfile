pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                branch 'master'
                git 'https://github.com/instana/robot-shop.git'
            }
        }
        stage('Build'){
            steps{
                script{
                    checkout scm
                    dir('user')
                    sh 'mvn test'
                }
            }
        }
        stage ('Imaging'){
            steps{
                script{
                    checkout scm
                    dir('web')
                    sh  'mvn clean package'
                    sh 'docker build -t webimage'
                }

            }
        }
    }
    post{
        success{
            echo 'Pipeline Successfully executed'
        }
        failure{
            echo 'Pipeline Successfully executed'
        }
    }
}

   
