node {
  stage('Scm Checkout') {
    git 'https://github.com/nareshbandapally916/my-app'
  }
   stage('Compile-Package') {
     def mvnHome = tool name: 'Maven3', type: 'maven'
     sh "${mvnHome}/bin/mvn clean compile package"
   }
}
