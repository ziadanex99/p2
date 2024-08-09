pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                git 'https://github.com/ziadanex99/DOV'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                script {
                    def tomcatUrl = 'http://localhost:9090/manager/text'
                    def tomcatUser = 'tomcat'
                    def tomcatPass = 'password'
                    def warFile = 'target/MyWebApp.war'

                    sh "curl -u ${tomcatUser}:${tomcatPass} --upload-file ${warFile} ${tomcatUrl}/deploy?path=/MyWebApp&update=true"
                }
            }
        }
    }
}
