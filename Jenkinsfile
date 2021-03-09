pipeline{
    agent any
    stages{
        stage('code checkout'){
            steps{
                git credentialsId: 'github', url: 'https://github.com/yuvin-ram/tomcat-practice.git'
            }
        }
        stage('code build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('code deploy'){
            steps{
                sshagent(['tomcatdeploy']){
                    sh 'scp -o StrictHostKeyChecking=no target/webapp.war ec2-user@172.31.25.141:/opt/tomcat/webapps'
                }
            }
        }
    }
}
