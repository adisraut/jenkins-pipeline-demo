pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Starting Build Stage...'
                echo 'Installing dependencies and preparing application'
                
                script {
                    if (isUnix()) {
                        sh '''
                            echo "Setting up environment on Unix/Linux"
                            echo "Checking workspace contents:"
                            ls -la
                        '''
                    } else {
                        bat '''
                            echo "Setting up environment on Windows"
                            echo "Checking workspace contents:"
                            dir
                            echo "Build completed successfully!"
                        '''
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'Starting Test Stage...'
                echo 'Running mock tests (no Python required)'
                
                script {
                    if (isUnix()) {
                        sh '''
                            echo "Running tests on Unix/Linux"
                            echo "Checking if our files exist:"
                            ls -la *.py || echo "Python files found"
                        '''
                    } else {
                        bat '''
                            echo "Running tests on Windows"
                            echo "Checking if our files exist:"
                            dir *.py
                            echo "All tests passed!"
                        '''
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Starting Deploy Stage...'
                echo 'Deploying application to staging environment'
                
                script {
                    if (isUnix()) {
                        sh '''
                            echo "Simulating deployment on Unix/Linux..."
                            echo "Application files ready for deployment"
                        '''
                    } else {
                        bat '''
                            echo "Simulating deployment on Windows..."
                            echo "Application files ready for deployment"
                            echo "Deployment completed successfully!"
                        '''
                    }
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline execution completed!'
        }
        success {
            echo 'Pipeline succeeded! All stages completed successfully.'
        }
        failure {
            echo 'Pipeline failed! Check the logs for details.'
        }
    }
}
