node("maven") {
  checkout scm
  stage("Test") {
    sh "mvn test"
  }
  stage("Deploy") {
    sh "mvn  -popenshift -DskipTests clean fabric8:deploy"
  }
}
