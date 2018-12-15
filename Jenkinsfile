node() {
stage('codecheckout'){
 
}
def mvnHome = tool 'MAVEN_HOME'
def os = System.properties['os.name'].toLowerCase()
stage('compile'){

    echo "OS: ${os}"
    if (os.contains("linux")) {
      sh "mvn compile" 
    } else {
      bat "${mvnHome}/bin/mvn clean compile" 
    }
}
stage('test'){
    if (os.contains("linux")) {
      sh "mvn test" 
    } else {
      bat "${mvnHome}/bin/mvn clean test" 
    }
    junit 'target\\surefire-reports\\*.xml'
}
 stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven-3', type: 'maven'
        withSonarQubeEnv('sonar-6') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
    }
stage('package'){
    if (os.contains("linux")) {
      sh "mvn package" 
    } else {
      bat "${mvnHome}/bin/mvn clean package" 
    }
  
    

