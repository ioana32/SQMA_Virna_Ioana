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
                    if (env.TEST_TO_RUN == 'ALL') {
                        sh 'python -m unittest discover tests'
                    } else if (env.TEST_TO_RUN == 'Test1') {
                        sh 'python -m unittest tests.test_case_1' 
                    } else if (env.TEST_TO_RUN == 'Test2') {
                        sh 'python -m unittest tests.test_case_2' 
                    } else {
                        echo 'Invalid test case'
                        exit 1
                    }
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
