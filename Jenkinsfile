pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '3353a1e2-8e07-43be-9f19-81d2299f5eb6', path: '', url: 'http://localhost:8080')], contextPath: '/ci -cd -jm', war: '**/*.war'}
 }
 }
 }
}
