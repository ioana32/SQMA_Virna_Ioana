pipeline {
    agent any 
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ioana32/SQMA_Virna_Ioana.git'
            }
        }

        stage('Run Unit Tests') {
            steps {
                script {
                    echo 'Running Unit Tests...'
                    bat 'C:\\Python\\Python313\\python.exe -m unittest discover tests'
                }
            }
        }

        stage('Run Test Case 1') {
            steps {
                script {
                    echo 'Running Test Case 1...'
                    bat 'C:\\Python\\Python313\\python.exe -m unittest tests.test_case_1'
                }
            }
        }

        stage('Run Test Case 2') {
            steps {
                script {
                    echo 'Running Test Case 2...'
                    bat 'C:\\Python\\Python313\\python.exe -m unittest tests.test_case_2'
                }
            }
        }        
    }
    post {
        always {
            cleanWs()
        }
    }
    
}
