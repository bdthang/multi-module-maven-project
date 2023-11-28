pipeline {
  agent any
  tools {
      maven 'maven-3.9.5'
  }
  stages {
    stage("Build") {
      steps {
        // git url: 'https://github.com/bdthang/multi-module-maven-project'
        withMaven {
          sh "mvn clean package"
        } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
      }
    }

    stage("Deploy") {
        steps {
            withMaven{
                sh "mvn deploy -DskipTests -DaltDeploymentRepository=nexus::default::http://nexus-neid.gtelict.local:8081/repository/maven-snapshots/"
            }
        }
    }
  }
}