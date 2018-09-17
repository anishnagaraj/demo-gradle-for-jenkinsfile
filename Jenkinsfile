def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
    containerTemplate(name: 'gradle', image: 'ticketfly:jenkins-example-gradle-build:latest', ttyEnabled: true, command: 'cat')
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
