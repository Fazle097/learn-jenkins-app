pipeline {
    agent any

    environment {
        npm_config_cache = './.npm-cache'
    }

    stages {
        stage('Build and Test inside Docker') {
            steps {
                script {
                    docker.image('node:18-alpine').inside('-u root:root') {
                        sh '''
                            ls -la
                            node --version
                            npm --version
                            npm ci
                            npm run build
                            test -f build/index.html
                            npm test
                        '''
                    }
                }
            }
        }
    }

}
