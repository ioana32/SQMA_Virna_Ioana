pipeline {
    agent any  // Rulează pe orice agent disponibil în Jenkins
    environment {
        // Definirea variabilelor de mediu
        TEST_TO_RUN = 'ALL'  // Poți schimba această valoare pentru a rula un anumit test
    }
    stages {
        stage('Checkout') {
            steps {
                // Clonăm repository-ul de pe GitHub
                git 'https://github.com/ioana32/SQMA_Virna_Ioana.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    // Instalăm dependențele necesare (de exemplu, din requirements.txt)
                    sh 'pip install -r requirements.txt'  // Asigură-te că ai requirements.txt în directorul tău
                }
            }
        }
        
        stage('Run Tests') {
            steps {
                script {
                    // Rulăm testele
                    if (env.TEST_TO_RUN == 'ALL') {
                        sh 'python -m unittest discover tests'  // Rulează toate testele din folderul 'tests'
                    } else if (env.TEST_TO_RUN == 'Test1') {
                        sh 'python -m unittest tests.test_case_1'  // Rulează testul specificat
                    } else if (env.TEST_TO_RUN == 'Test2') {
                        sh 'python -m unittest tests.test_case_2'  // Rulează testul specificat
                    } else {
                        echo 'Invalid test case'
                        exit 1
                    }
                }
            }
        }

        stage('Archive Test Results') {
            steps {
                // Arhivăm rezultatele testelor (pentru a le vizualiza în Jenkins)
                junit '**/test-*.xml'  // Asigură-te că generăm fișiere de rezultate cu sufixul "test-*.xml"
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
