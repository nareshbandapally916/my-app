node {
  stage('Scm Checkout') {
    git 'https://github.com/nareshbandapally916/my-app'
  }
   stage('Compile Package') {
     def mvnHome = tool name: 'Maven3', type: 'maven'
     sh "${mvnHome}/bin/mvn clean compile package"
   }
  stage('Email Notifications') {
    mail bcc: '', body: 'Welcome to Jenkins Job', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'nareshbandapallybr@gmail.com'
  }
}
