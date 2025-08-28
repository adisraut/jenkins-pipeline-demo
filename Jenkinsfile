pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Starting Build Stage...'
                echo 'Installing dependencies and preparing application'
                
                // For Python projects, you might install dependencies here
                script {
                    if (isUnix()) {
                        sh '''
                            echo "Setting up Python environment"
                            python3 --version || python --version
                            echo "Build completed successfully!"
                        '''
                    } else {
                        bat '''
                            echo "Setting up Python environment"
                            python --version
                            echo "Build completed successfully!"
                        '''
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'Starting Test Stage...'
                echo 'Running unit tests'
                
                script {
                    if (isUnix()) {
                        sh '''
                            echo "Running Python tests"
                            python3 -m pytest test_app.py -v || python -m unittest test_app.py -v
                            echo "All tests passed!"
                        '''
                    } else {
                        bat '''
                            echo "Running Python tests"
                            python -m unittest test_app.py -v
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
                            echo "Simulating deployment..."
                            echo "Running the application"
                            python3 app.py || python app.py
                            echo "Deployment completed successfully!"
                        '''
                    } else {
                        bat '''
                            echo "Simulating deployment..."
                            echo "Running the application"
                            python app.py
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
