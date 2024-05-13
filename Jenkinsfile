node {
  stage('Scm Checkout') {
    git 'https://github.com/nareshbandapally916/my-app'
  }
   stage('Compile-Package') {
     tools { 
       maven 'Maven3'
     }
     sh 'mvn package'
   }
}
    
