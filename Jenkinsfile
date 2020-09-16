pipeline{
    agent any
    tools {nodejs "node"}
    stages{
        stage("Get code from Github"){
            steps{
                echo "Checking out code from Github"
                git credentialsId: '4d7078da-78cf-4cc5-9111-003196355f4d', url: 'https://github.com/nitingupta220/travis-ci-demo.git'
            }
        }
        stage("Install the dependencies"){
            steps{
                echo "Installing the dependencies"
                sh "npm install"
            }
            post{
                success{
                    echo "Dependencies Installed Successfully"
                }
                failure{
                    echo "Dependencies Installed Failed"
                }
        
            }
        }
        stage("Deploying to Github pages"){
            steps{
                echo "Deploy started"
                sh "npm run deploy"
            }
            post{
                success{
                    echo "Deploy successful"
                }
                failure{
                    echo "Deploy failed"
                }
            }
        }
    }
}