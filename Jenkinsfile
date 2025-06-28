pipeline {
    agent any

    environment{
        SECRET_TOKEN = credentials('secret_token')
    }

    stages {

        stage('qws-cli'){

            agent {
                docker {
                    image 'amazon/aws-cli'
                    args "--entrypoint=''"
                }
                steps{
                    sh '''
                        aws --version
                    '''
                }
            }

        }
        // stage('Build') {
        //     agent{
        //         docker{
        //             image 'node:18-alpine'
        //             reuseNode true
        //         }
        //     }
        //     steps {
        //         sh '''
        //         npm --version
        //         node --version
        //         npm ci
        //         npm run build

        //         '''
        //     }
        // }

        // stage('Test'){
        //     agent{
        //         docker{
        //             image 'node:18-alpine'
        //             reuseNode true
        //         }
        //     }
        //     steps{
        //         sh '''
        //         echo "Test stage"
        //         test -f 'build/index.html'
        //         npm test

        //         '''
        //     }
        // }
        //  stage('E2E'){
        //     agent{
        //         docker{
        //             image 'mcr.microsoft.com/playwright:v1.53.0-noble'
        //             reuseNode true
        //         }
        //     }
        //     steps{
        //         sh '''
        //         echo $SECRET_TOKEN
        //             # npm install serve
        //             # node_modules/.bin/serve -s build &
        //             #sleep 10
        //             # npx playwright test
              
        //         '''
        //     }
        // }
    }

    post{
        always{
            junit 'jest-results/junit.xml'
        }
    }
}
