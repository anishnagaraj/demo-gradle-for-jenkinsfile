def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
    containerTemplate(name: 'gradle', image: 'frekele/gradle:4.8-jdk8', ttyEnabled: true, command: 'cat')
  ]) {

    node(label) {
        stage('Preparation') {
            git 'https://github.com/anishnagaraj/demo-gradle-for-jenkinsfile.git'
        }
        container('gradle') {
                stage('Build') {
                    sh 'gradle build'
                }
        }
        
    }
}
