pipeline {
    agent { label 'JDK-8'}
    triggers {
        pollSCM('* * * * * ')
    }
    tools {
       maven 'maven3.6', 
       jdk 'JDK-8' 
    }
    stages { 
        stage('git') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/Nagabhavani818/game-of-life.git'
            }
        }
        stage('package') {
            steps {
                sh script: 'mvn package'
            }
        }
        stage('Test results') {
            steps {
                archiveArtifacts artifacts : '**/target/gameoflife-*.jar'
                junit testResults : '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }
}
