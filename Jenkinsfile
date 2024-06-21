pipeline {
    agent any

    stages {
        // This is build phase
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
                '''
            }
        }

        stage('Run Tests') {
            parallel {
                stage('Test') {
                    /*
                        This is test phase with docke
                    */
                    agent {
                        docker {
                            image 'node:18-alpine'
                            reuseNode true
                        }
                    }
                    steps {
                        sh '''
                            echo "Testing Phase"
                            echo `pwd`
                            # echo "${?}"
                        '''
                    }

                }
            }
        }    
    }
}
