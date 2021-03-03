pipeline {
    agent {
        docker {
            image 'paularbb/rubywd'
        }
    }
    
    stages {
       
       stage ('Build')   {
           steps {
               echo 'Building or Resolve Dependencies!'
               sh 'rm -f Gemfile.lock'
               sh 'bundle install'
           }
       }
       
       stage ('Test') {
           steps {
               echo 'Running regression tests!'
               sh 'cucumber -p ci'
           }
       }
       
       stage ('UAT') {
           steps {
               echo 'Wait for User Accepctance'
               input(message:'Go to Production?', ok: 'Yes')
           }
       }
       
       stage ('Prod') {
           steps {
               echo 'WebApp is ready :) '
           }
       }
       
    }
    
}
