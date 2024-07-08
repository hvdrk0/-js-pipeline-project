pipeline {
   agent any
   parameters {
      choice(name: 'VERSION', choices: ['1.0.0','1.2.0','2.0.0'], description: '')
      booleanParam(name: 'executeTests', defaultValue: true, description: '')
   }
   stages {
      stage("init") {
         steps {
            script {
               gv = load "script.groovy"
               echo 'loading'
            }
         }
      }
      stage("build") {
         steps {
            script {
               gv.buildApp()
            }
         }
      }
      stage("test") {
         when {
            expression {
               params.executeTests
            }
         }
         steps {
            script {
               gv.testApp()
            }
         }
      }
      stage("deploy") {
         steps {
            script {
               gv.deployApp()
            }
         }
      }
   }
}
