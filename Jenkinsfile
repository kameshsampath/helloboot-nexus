podTemplate(name: 'maven33', label: 'maven33', cloud: 'openshift',serviceAccount: 'helloboot', containers: [
    containerTemplate(name: 'jnlp',
                image: 'openshift/jenkins-slave-maven-centos7',
                workingDir: '/tmp',
                envVars: [
                    envVar(key: 'MAVEN_MIRROR_URL',value: 'http://nexus/nexus/content/groups/public/')
                ],
                cmd: '',
                args: '${computer.jnlpmac} ${computer.name}')
]){
  node("maven33") {
    checkout scm
    stage("Test") {
      sh "mvn test"
    }
    stage("Deploy") {
      sh "mvn  -Popenshift -DskipTests clean fabric8:deploy"
    }
  }
}