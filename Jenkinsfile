pipeline{
    agent any
    tools{
        maven "maven3.8.8"
    }
    stages{
        stage("1. Git clone from repo"){
            steps{
                sh "echo start of git clone"
                git branch: 'main', url: 'https://github.com/annorakrofi/web-app.git'
                sh "echo end of git clone"
            }
        }
        stage("2.0 Build from Maven"){
    
                steps{
                    sh "echo start building from Maven"
                    sh "mvn clean package"
                    sh "echo end of build"
                }
            
        }
        stage("3.0 Code Scan"){
            steps{
                sh "echo start  of code scan"
                sh "mvn sonar:sonar"
                sh "echo end of code scan"
            }
            
        }
        stage("4.0 Store Artifact"){
            steps{
                sh "echo Deploy artifact"
                sh "mvn deploy"
            }
        }
        // stage("5.0 Deployment to tomcat UATT"){
        //     steps{
        //         sh "echo start of tomcat deployment"
        //          deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://172.31.23.167:8080/')], contextPath: null, war: 'target/*.war'
        //          sh "echo end of tomcat deployment"
        //     }
        // }
    }
}
