pipeline {
    agent any

    tools {
        maven 'mvn-3.5.4'
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