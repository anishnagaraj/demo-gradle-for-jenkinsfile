def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
    containerTemplate(name: 'gradle', image: 'gradle:jdk8-alpine', ttyEnabled: true, command: 'cat')
  ]) {

    node(label) {
        stage('Preparation') {
            git 'https://github.com/anishnagaraj/demo-gradle-for-jenkinsfile.git'
        }
        container('maven') {
                stage('Build') {
                    sh 'mvn package'
                }
        }
        stage('Results') {
            junit '**/target/surefire-reports/TEST-*.xml'
            archive 'target/*.jar'
        }
        
    }
}
