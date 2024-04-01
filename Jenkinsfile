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





       
     }
}
