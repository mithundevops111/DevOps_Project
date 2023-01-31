pipeline {
    agent any
    tools{
        maven "maven"
    }

    stages {
        stage('Git Clone') {
            steps {
                echo 'Cloning the source code from Github'
                git credentialsId: 'github', url: 'https://github.com/mithundevops111/DevOps_Project.git'
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Build using Maven Tool'
                sh 'mvn package'
            }
        }
        stage('Tomcat Deployment') {
            steps {
                echo 'Tomcat Deployment'
                deploy adapters: [tomcat9(credentialsId: 'tomcat9', path: '', url: 'http://18.117.123.161:8080')], contextPath: null, war: '*/*.war'
            }
        }
    }
}
