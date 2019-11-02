node()
{
    
    //echo "GitHub BranhName ${env.BRANCH_NAME}"
  //echo "Jenkins Job Number ${env.BUILD_NUMBER}"
  echo "Jenkins Node Name ${env.NODE_NAME}"
  
  echo "Jenkins Home ${env.JENKINS_HOME}"
  echo "Jenkins URL ${env.JENKINS_URL}"
  echo "JOB Name ${env.JOB_NAME}"
    
def MavenHome = tool name : 'maven 3.6.1' , type : 'maven'
properties([
    buildDiscarder(logRotator(numToKeepStr: '7')),
    pipelineTriggers([
        pollSCM('* * * * *')
    ])
])
    stage('CheckOutCode')
    {
        git credentialsId: 'b5fc47f3-bf19-4692-96bd-8c46d20e5155', url: 'https://github.com/bishnu9776/maven-web-application.git'
    }
    stage('Build')
    {
        sh "${MavenHome}/bin/mvn clean package"
    }
    stage('EmailNotification')
    {
        emailext body: 'build is done in body tag', subject: 'build is done', to: 'bishnu.green.green@gmail.com, bishnudev9776@gmail.com'
    }
}
