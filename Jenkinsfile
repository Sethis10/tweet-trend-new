//def registry = 'https://ssdev.jfrog.io/'
//def imageName = 'ssdev.jfrog.io/valaxy-docker-local/ttrend'
//def version   = '2.1.2'
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
        stage("Build") {
            steps {
                echo "------------- Build Started -----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'  // Corrected Maven command
                echo "------------- Build Completed ---------"
            }
        }
    }
}
        /*
        stage("Jar Publish") {
            steps {
                script {
                    echo '<--------------- Jar Publish Started --------------->'
                    def server = Artifactory.newServer url: "${registry}artifactory", credentialsId: "4fc0532f-db91-4657-ab5a-e5bc27c67614"
                    def properties = "buildid=${env.BUILD_ID},commitid=${env.GIT_COMMIT}"
                    def uploadSpec = """{
                          "files": [
                            {
                              "pattern": "jarstaging/(*)",
                              "target": "maven-local-libs-release-local/{1}",
                              "flat": "false",
                              "props": "${properties}",
                              "exclusions": ["*.sha1", "*.md5"]
                            }
                          ]
                     }"""
                    def buildInfo = server.upload(uploadSpec)
                    buildInfo.env.collect()
                    server.publishBuildInfo(buildInfo)
                    echo '<--------------- Jar Publish Ended --------------->'
                }
            }
        }

        stage(" Docker Build ") {
            steps {
                script {
                    echo '<--------------- Docker Build Started --------------->'
                    app = docker.build(imageName+":"+version)
                    echo '<--------------- Docker Build Ends --------------->'
                }
            }
        }

        stage (" Docker Publish "){
            steps {
                script {
                    echo '<--------------- Docker Publish Started --------------->'  
                    docker.withRegistry(registry, '4fc0532f-db91-4657-ab5a-e5bc27c67614'){
                    app.push()
                }    
                    echo '<--------------- Docker Publish Ended --------------->'  
                }
             }
        }
    }
}
*/
