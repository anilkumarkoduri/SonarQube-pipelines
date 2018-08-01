node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
    git credentialsId: 'Github-ID', url: 'https://github.com/pavants52/SonarQube-pipelines.git'
   }
   stage('Build') {
     withMaven(jdk: 'Java', maven: 'maven') {
       sh 'mvn clean compile'
     }
   }
   stage('Unit Test') {
     withMaven(jdk: 'Java', maven: 'maven') {
       sh 'mvn test'
     }
   }
  stage('SonarQube Analysis') {
     // def job = build job: 'SonarJob'
     // withSonarQubeEnv("SonarQube") {
      }
      withMaven(jdk: 'Java', maven: 'maven') {
          sh ' mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=pavants52 '+ 
             ' -Dsonar.login=2eb6424b017f76ec050f6085eb95e2877f3b5ed5 '
          }
      } 
   
    //stage("Quality Gate"){
          //timeout(time: 1, unit: 'HOURS') {
             // def qg = waitForQualityGate()
              //if (qg.status != 'OK') {
                //  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              //}
         // }
     // }
   
    stage('Archival') {
      withMaven(jdk: 'Java', maven: 'maven') {
       //sh 'mvn package'
     }
   }
     stage('Deploy to Artifactory Repo') {
     }

   
    stage('Deploy to Dev') {
      
   }
   stage('Smoke Test Execution') {
      
   }

    
}
