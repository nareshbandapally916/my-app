properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '2')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], parameters([choice(choices: ['master', 'develop'], description: 'github branches for my-app repository', name: 'branch')])])
node {
  stage('Scm Checkout') {
    git 'https://github.com/nareshbandapally916/my-app'
  }
   stage('Compile Package') {
     def mvnHome = tool name: 'Maven3', type: 'maven'
     sh "${mvnHome}/bin/mvn clean compile package"
  }
 /* stage('Sonar Analysis') {
     def mvnHome = tool name: 'Maven3', type: 'maven'
     withSonarQubeEnv(sonar-6) {
       sh "${mvnHome}/bin/mvn sonar:sonar"
     }
  } */
  /* stage('Email Notifications') {
    mail bcc: '', body: 'Welcome to Jenkins Job', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'nareshbandapallybr@gmail.com'
  } */
  stage('Slack Notification') {
    slackSend baseUrl: 'https://hooks.slack.com/services/', 
              channel: '#devops-automation', 
              color: 'good', 
              message: 'Welcome to Jenkins, Slack!', 
              tokenCredentialId: 'slack-demo', 
              username: 'naresh bandapally'
  }

stage('Deploy to Tomcat') {
      sshagent(['tomcat-app']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@172.31.57.217:/opt/apache-tomcat-10.1.24/webapps/'
      }
   }
  
}
