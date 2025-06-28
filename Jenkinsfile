pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                npm --version
                node --version
                npm ci
                npm run build

                '''
            }
        }

        stage('Test'){
            steps{
                sh '''
                echo "Test stage"
                if [ -f build/index.html ]; then
                    echo "✅ File exists"
                    else
                    echo "❌ File not found"
                    exit 1
                fi

                '''
            }
        }
    }
}
