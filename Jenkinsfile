#! groovy

pipeline {
    agent any
    environment {
        LC_ALL = 'en_US.UTF-8'
    }
    stages {
      stage('Setup') {
        steps {
            echo "Setup"
            // Install bundler in order to use fastlane
            sh "gem install bundler -n /usr/local/bin"
            dir("android") {
                    // sh "pwd"
            sh "bundle config set --local path 'vendor/bundle'"
            // install bundles if they're not installed
            sh "bundle check || bundle install --jobs=4 --retry=3"
                    }
            // set the local path for bundles in vendor/bundle
            
            }
        }

        stage('Build') {
            steps {
                echo "Building"
                // sh "cd android"
                dir("android") {
                    // sh "pwd"
                    sh 'gradle init'
                    sh "echo 'building..'"
                    // withGradle {
                        // sh 'gradle wrapper build'
                         sh "bundle exec fastlane distributeProd"
                        // }
                   
                    }
                
                }
            }
    }
}