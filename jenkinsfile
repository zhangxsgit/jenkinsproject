pipeline { 
    agent any 
    stages { 
        stage('Checkout') { 
            steps { git url: 'https://github.com/zhangxsgit/jenkinsproject.git', branch: 'main' }    
        } 
        stage('Install Dependencies') { 
            parallel { 
                stage('Install Requirements') {
                    steps { sh 'pip install -r requirements.txt || echo "No requirements.txt found, skipping"' } 
                } 
                stage('Lint Code') { 
                    steps { sh 'pip install flake8 && flake8 hello.py || echo "Linting skipped or failed"' } 
                }    
            }    
        } 

        stage('Build and Run') { 
            steps { sh 'python3 hello.py' }    
        } 
        stage('Archive Artifacts') { 
            steps { archiveArtifacts artifacts: 'hello.py, test-results.xml', allowEmptyArchive: true }    
        }    
    }    
}
