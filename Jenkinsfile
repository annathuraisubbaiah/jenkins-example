pipeline {
    agent any

    stages {
        stage ('Compile Stage') {
            stage ('Build') {
                git url: 'https://github.com/cyrille-leclerc/multi-module-maven-project'
                withMaven {
                  sh "mvn clean verify"
                } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
              }
           // steps {
              //  withMaven(maven : 'maven_3_5_0') {
                //    sh 'mvn clean compile'
               // }
           // }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}