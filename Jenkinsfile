node{
   stage('SCM Checkout'){
     git 'https://github.com/snagarajudmm/my-app.git'
   }
 stage('Compile'){
      sh "mvn compile"
    }
 }
 stage('SonarQube Analysis') {
          sh "mvn sonar:sonar" 
        }
  
    

