pipeline {
    agent any
    tools {
        maven "Maven_Home"
        }
    stages {
        stage('Checkout') {                       
            steps{
            git branch: 'main', credentialsId: 'git_Credentials', url: 'https://github.com/Shubham4676/webrepo.git'
                echo 'Checkout Success'
            }
        }
        
        stage('MavenBuild') {
            steps{
            sh 'mvn clean install'
                echo 'Build Success'
            }
        }
        
        stage('Deploy') {
            steps{
        sshagent(['deploy_user']) {
        
        sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/CICDJOB-3/webapp/target/webapp.war  ec2-user@52.53.195.59:/opt/apache-tomcat-9.0.84/webapps"
                echo 'Deploying Success'  
            }
            
            }
        }
    }
}
