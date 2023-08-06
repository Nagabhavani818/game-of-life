pipeline {
    agent { label 'JDK-8'}
    triggers {
        pollSCM('* * * * * ')
    }
    tools {
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
                archiveArtifacts artifacts : '**/target/gameoflife-*.war'
                junit testResults : '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }
}
