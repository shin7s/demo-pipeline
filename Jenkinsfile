pipeline {
    agent any

    tools {
        maven 'mvn-3.6.3'
    }
    stages {
        stage('build') {
            steps {
                sh "mvn clean package spring-boot:repackage"
                sh "printenv" //输出环境变量
            }
        }
    }
}