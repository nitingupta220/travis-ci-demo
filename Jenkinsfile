pipeline{
    agent any
    tools {nodejs "node"}
    stages{
        stage("Get code from Github"){
            steps{
                echo "Checking out code from Github"
                git credentialsId: '1c75fb7c-c157-46c9-8ebc-5175d38d2871', url: 'https://github.com/nitingupta220/travis-ci-demo.git'
            }
        }
        stage("Install the dependencies"){
            steps{
                echo "Installing the dependencies"
                sh "npm ci"
                sh "npm run cy:verify" 
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
        // stage("cypress parallel tests"){
        //     environment {
        //         CYPRESS_RECORD_KEY = credentials('cypress-record-key')
        //         CYPRESS_trashAssetsBeforeRuns = 'false'
        //     }
        //     parallel {
        //         stage("Tester A"){
        //             steps{
        //                 echo "Running build ${env.BUILD_ID}"
        //                 sh "npm run cy:run"
        //             }
        //         }
        //     }
        // }
        stage("Deploying to Github pages"){
            steps{
                echo "Deploy started"
                sh "npm run deploy"  
            }
            // post{
            //     success{
            //         echo "Deploy successful" 
            //         emailext body: '${DEFAULT_CONTENT}', subject: 'Jenkins Job', to: 'nitin16@navgurukul.org' 
            //         // Sending message to slack
            //         slackSend color: 'good', channel: '#test-jenkins', message: "*${currentBuild.currentResult}:* Job ${JOB_NAME} build ${BUILD_NUMBER}\n More info at: ${BUILD_URL}"
            //     }
            //     failure{
            //         echo "Deploy failed"
            //         slackSend color: 'danger', channel: '#test-jenkins', message: "*${currentBuild.currentResult}:* Job ${JOB_NAME} build ${BUILD_NUMBER}\n More info at: ${BUILD_URL}"
            //     }
            // }
        }
    }
}