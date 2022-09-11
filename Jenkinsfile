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

            steps {
                sh "jf rt upload --url http://192.168.0.104:8082/artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN} /artifactory/valaxy/"
            }
        }

    }

    }


