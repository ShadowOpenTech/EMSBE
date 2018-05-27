 node {
   //def mvnHome
   
   /*parameters{
       string(name: 'gitURL', defaultValue: '${gitURL}', description: 'Git url for cloning')
    }
     
    stage('Print ip param'){
        echo ${params.gitURL}
    } */
    stage('Preparation') { 
      // Get some code from a GitHub repository
      git 'https://github.com/ShadowOpenTech/EMSBE.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.  
      
      //mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
          bat 'echo %PATH%'
            bat 'set JAVA_HOME "C:\\Users\\nandh\\scoop\\apps\\openjdk\\1.8.0.161-1\\"'
            //bat(/"C:\Users\nandh\scoop\apps\maven\current\bin\mvn" -Dmaven.test.failure.ignore clean package/)
            bat 'mvn -version'
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
