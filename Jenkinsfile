pipeline {
    agent any
    stages {
        stage('Build') {
            agent any
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            }
        }
        stage('Test') {
            agent any
            steps {
                sh 'python test_calc.py'
            }

        }
        stage('Deliver') {
            agent any
            steps {
                sh 'pyinstaller --onefile sources/add2vals.py'
            }
            post {
                success {
                    archiveArtifacts 'dist/add2vals'
                }
            }
        }
    }
}
