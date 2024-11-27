pipeline {
    agent {
        node {
            label 'maven'  // Ensure the 'maven' label corresponds to a valid Jenkins agent node
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH" 
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}
