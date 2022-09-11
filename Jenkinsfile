pipeline{
    agent any

    environment {
        CI = true
        ARTIFACTORY_ACCESS_TOKEN = credentials('artifactory-access-token')
    }

    stages{
        stage('build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('upload to artifactory'){
            agent {
                docker {
                    image 'releases-docker.jfrog.io/jfrog/jfrog-cli-v2:2.2.0'
                    reuseNode true
                }

            }
            steps {
                sh "jfrog rt upload --url http://'192.168.0.104:8082/artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN} target/demo-1.0.war valaxy/"
            }
        }

    }

    }
