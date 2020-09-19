pipeline{
    agent any
    tools {nodejs "node"}
    stages{
        // stage("Get code from Github"){
        //     steps{
        //         echo "Checking out code from Github"
        //         git credentialsId: '4d7078da-78cf-4cc5-9111-003196355f4d', url: 'https://github.com/nitingupta220/travis-ci-demo.git'
        //     }
        // }
        // stage("Install the dependencies"){
        //     steps{
        //         echo "Installing the dependencies"
        //         sh "npm ci"
        //         sh "npm run cy:verify"
        //     }
        //     post{
        //         success{
        //             echo "Dependencies Installed Successfully"
        //         }
        //         failure{
        //             echo "Dependencies Installed Failed"
        //         }
        
        //     }
        // }
        // stage("cypress parallel tests"){
        //     environment {
        //         CYPRESS_RECORD_KEY = credentials('cypress-record-key')
        //         CYPRESS_trashAssetsBeforeRuns = 'false'
        //     }
        //     parallel {
        //         stage("Tester A"){
        //             steps{
        //                 // echo ""
        //                 echo "Running build ${env.BUILD_ID}"
        //                 sh "npm run cy:run"
        //             }
        //         }
        //     }
        // }
        stage("Deploying to Github pages"){
            steps{
                echo "Deploy started"
                // sh "npm run deploy"
            }
            post{
                success{
                    echo "Deploy successful" 
                    // mail bcc: '', body: 'Build Successful', cc: '', from: 'nitingupta220@gmail.com', replyTo: '', subject: 'Jenkins Job', to: 'nitin16@navgurukul.org'
                    emailext body: '${DEFAULT_CONTENT}', subject: 'Jenkins Job', to: 'nitin16@navgurukul.org'
                }
                failure{
                    echo "Deploy failed"
                }
            }
        }
    }
}