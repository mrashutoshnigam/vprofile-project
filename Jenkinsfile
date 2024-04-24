pipeline {
    agent any
    tools {
        maven 'MAVEN3'
        jdk 'OracleJDK8'
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'ashutosh456'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.50.16'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexus_login'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo 'Build Success'
                    echo 'Now Archiving'
                    archiveArtifacts artifacts: '**/*.war'
                }
                failure {
                    echo 'Build Failed'
                }
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test'
            }
            post {
                success {
                    echo 'Test Success'
                }
                failure {
                    echo 'Test Failed'
                }
            }
        }
        stage('Checkstyle Ananlysis'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
            post {
                success {
                    echo 'Checkstyle Analysis Success'
                }
                failure {
                    echo 'Checkstyle Analysis Failed'
                }
            }
        }
    }
}
