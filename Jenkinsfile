pipeline { 
    agent any 
    options {
      buildDiscarder logRotator(artifactDaysToKeepStr:'',artifactNumToKeepStr:'5',daysTokeepStr:'',numToKeepStr:'5')
      disableConcurrentBuilds()
    }
    stages { 
        stage('Hello') { 
            steps {
              echo "hello"
            }
        }
    }         
}
