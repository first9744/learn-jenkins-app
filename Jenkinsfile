pipeline {
    agent any

    environment {
        NETLIFY_SITE_ID = '9d51c6bc-d00b-458e-ba35-29a24141df86'
    }

    stages {

        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Tests') {
            parallel {
                stage('Unit tests') {
                    agent {
                        docker {
                            image 'node:18-alpine'
                            reuseNode true
                        }
                    }

                    steps {
                        sh '''
                            #test -f build/index.html
                            npm test
                        '''
                    }
                    // post {
                    //     always {
                    //         junit 'jest-results/junit.xml'
                    //     }
                    // }
                }
            }
        }
    }
}
