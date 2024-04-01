pipeline {
  agent any
     stages {
       
         stage('Git checkout') {
            steps {
               echo 'This is for cloning the gitrepo'
               git branch: 'main', url: 'https://github.com/DeviSaiSwethaKonijeti/InsureMe-20Mar'
                          }
                   }
         stage('Create a Package') {
            steps {
               echo 'This will create a package using maven'
               sh 'mvn package'
                             }
                  }


          stage('generating HTML reports') {
            steps {
                 publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/Insurance project/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])

                             }
                  }
            stage('Create a Docker image from the Package Insure-Me.jar file') {
                 steps {
                    sh 'docker build -t devisaiswetha/insure-me:1.0 .'
                    }
            }
       
            stage('Login to Dockerhub') {
                 steps {
                  withCredentials([usernamePassword(credentialsId: 'a3295102-7f5f-4778-a899-516a317def2d', passwordVariable: 'password', usernameVariable: 'username')]) {
                   sh 'docker login -u ${username} -p {password} 
                                                    }
                         }
            }




       
                             

       
     }
}
