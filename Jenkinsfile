node('default-agent') {
    currentBuild.result = "SUCCESS"

       stage('Checkout'){

          checkout scm
       }

       stage('Test'){

         env.NODE_ENV = "test"

         print "Environment will be : ${env.NODE_ENV}"

         sh 'ruby -v'
         sh 'bundle install'
         sh 'jekyll build'

       }
}