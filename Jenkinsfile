pipeline { 
    agent any 
    environment {
        // Add Homebrew bin to PATH (adjust for Intel/Apple Silicon)
        PATH = "/opt/homebrew/bin:${env.PATH}"
    }
    stages { 
        stage('Checkout') { 
            steps { git url: 'https://github.com/zhangxsgit/jenkinsproject.git', branch: 'main' }    
        } 
        stage('syntax check') { 
            steps { sh 'flake8 hello.py || echo "Linting skipped or failed"' }   
        } 
        stage('Build and Run') { 
            steps { sh 'python3 hello.py' }    
        } 
        stage('Archive Artifacts') { 
            steps { archiveArtifacts artifacts: 'hello.py, test-results.xml', allowEmptyArchive: true }    
        }    
    }    
}
