pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH"  // Ensure this is correct
    }
    stages {
        stage("build") {
            steps {
                echo "------------- build started -----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'  // Corrected Maven command
                echo "------------- build completed ---------"
            }
        }
    }
}
