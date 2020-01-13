pipeline {
    agent any

    tools {
        maven 'mvn-3.5.4'
    }
    stages {
//         stage('build') {
//             steps {
//                 sh "mvn clean package spring-boot:repackage"
//                 sh "printenv" //输出环境变量
//             }
//         }

        stage('Code Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh """
                    mvn clean package org.sonarsource.scanner.maven:sonar-maven-plugin:3.4.1.1168:sonar \
                    -Dsonar.host.url=${SONAR_HOST_URL} \
                    -Dsonar.login=${SONAR_AUTH_TOKEN}
                    """
                }
            }
        }

        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}