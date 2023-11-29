#! groovy

pipeline {
    agent any
    stages {
      stage('Setup') {
        steps {
            echo "Setup"
            // Install bundler in order to use fastlane
            sh "gem install bundler"
            // set the local path for bundles in vendor/bundle
            sh "bundle config set --local path 'vendor/bundle'"
            // install bundles if they're not installed
            sh "bundle check || bundle install --jobs=4 --retry=3"
            }
        }

        stage('Build') {
            steps {
                echo "Building"
                // sh "cd android"
                dir("android") {
                    // sh "pwd"
                    sh "bundle exec fastlane distributeProd"
                    }
                
                }
            }
    }
}