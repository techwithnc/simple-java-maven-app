def mygvscript
pipeline {
    agent any
    environment {
        IMAGE_NAME = ""
        APP_VERSION = ""
    }
    tools{
        maven '01Maven'
    }
    stages{
        stage("Prepare"){
            steps{
                script{
                    mygvscript = load "script.groovy"
                }
            }
        }
        stage("Build_App"){
            steps{
                script{
                    mygvscript.buildApp()
                    sh "echo Hello!"
                    sh "ls -l"
                    APP_VERSION = readMavenPom().getVersion()
                    echo "VERSION: ${APP_VERSION}"
                    // def MATCHER = readFile(file: 'pom.xml' =~ '<version>(.+)</version>')
                    // println(MATCHER)
                    // MATCHER = readFile(file: 'pom.xml') =~ '<version>(.+)</version>'
                    // sh "echo ${env.MATCHER}"
                    // APP_VERSION = MATCHER[0][1]
                    // sh "echo ${env.APP_VERSION}"
                    // IMAGE_NAME = "$APP_VERSION-$BUILD_NUMBER"
                    // sh "echo ${env.IMAGE_NAME}"
                }
            }
        }
        // stage("Build_IMAGE"){
        //     steps {
        //         script {
        //             mygvscript.buildImage()
        //         }
        //     }
        // }
        // stage("Build_IMAGE"){
        //     steps {
        //         script {
        //             mygvscript.buildImage()
        //         }
        //     }
        // }  
        // stage("Push_IMAGE") {
        //     steps {
        //         script {
        //             mygvscript.pushImage()
        //         }
        //     }
        // }
    }
}
 