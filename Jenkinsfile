pipeline {
    agent any 
    environment {
        TEST_TO_RUN = 'ALL' 
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ioana32/SQMA_Virna_Ioana.git'
            }
        }

         stage('Run Tests') {
            steps {
                script {
                    bat 'C:\Python\Python313\python.exe -m unittest discover tests'
                    } 
                }
            }
        
    }
    post {
        always {
            // Curățăm workspace-ul Jenkins după fiecare rulare
            cleanWs()
        }
    }
}
