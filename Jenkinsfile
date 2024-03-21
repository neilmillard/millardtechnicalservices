node('default-agent') {
    currentBuild.result = "SUCCESS"

       stage('Checkout'){

          checkout scm
       }

       stage('PreReq'){
        sh 'ruby -v'
        sh 'bundle install'
        sh 'wget -O stout -q https://github.com/EagerIO/Stout/releases/download/v1.3.0/stout-linux'
        sh 'chmod +x ./stout'
       }

       stage('Build'){
         env.BUCKET = "www.millardtechnicalservices.co.uk"

         print "Deploy bucket will be : ${env.BUCKET}"

         sh 'ruby -v'
         sh 'bundle install'
         sh 'jekyll build'
       }

       stage('Deploy'){
         sh '#./stout deploy --bucket ${env.BUCKET} --key $AWS_KEY --secret $AWS_SECRET --region eu-west-1 --root ./_site'
       }
}