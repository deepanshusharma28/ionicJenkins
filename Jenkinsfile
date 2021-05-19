pipeline {

    agent any

    environment {
        PATH='/usr/local/bin:/usr/bin:/bin'
	}

    stages {

      stage('Switch Node Version'){
            steps{
               sh 'sudo n 10.16.0'
            }
         }
      stage('Copy static files from working project'){
         steps{
            sh 'cp /Users/administrator/Documents/Projects/hero-projects/Employee_app_ios/employeeapp/platforms/* .'
            sh 'cp /Users/administrator/Documents/Projects/hero-projects/Employee_app_ios/employeeapp/plugins/* .'
            sh 'cp /Users/administrator/Documents/Projects/hero-projects/Employee_app_ios/employeeapp/config.xml .'
            sh 'cp /Users/administrator/Documents/Projects/hero-projects/Employee_app_ios/employeeapp/package-json.xml .'
            sh 'cp /Users/administrator/Documents/Projects/hero-projects/Employee_app_ios/employeeapp/GoogleService-Info.plist .'
         }
      }
       stage('NPM Setup') {
          steps {
             sh 'npm install'
         }
       }

       stage('IOS Build') {
          steps {
             sh 'ionic cordova build ios --release'
             
          }
       }

       stage('Android Build') {
          steps {
               sh 'export JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home'
               sh 'echo $JAVA_HOME'
               sh 'ionic cordova build android --release'
               
          }
       }

       stage('APK Sign') {
          steps {
            // sh 'jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
              echo "Android"
          }
       }



      stage('Stage Web Build') {
          steps {
              sh 'npm run build --prod'
          }
       }

         stage('Publish Firebase Web') {
          steps {
              //sh 'firebase deploy --token "YourTokenKey"'
              echo 'Firebase Deploy'
          }
       }

        stage('Publish iOS') {
          steps {   
              echo "Publish iOS"
          }
       }

        stage('Publish Android') {
          steps {
              echo "Publish Android"
          }
       }


}
}

