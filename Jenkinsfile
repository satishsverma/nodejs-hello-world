node {

    Git_Branch = "${GIT_BRANCH}"
    appName = "satishsverma/demo"
    IMAGETAG = "${BUILD_VERSION}"
    ImageName = "${appName}:${IMAGETAG}"
    env.BUILDIMG = "${ImageName}"
    
    stage('Clone repository') {
        checkout scm
        sh "git checkout ${Git_Branch}"
    }

    stage('Build image') {
        app = docker.build("${env.BUILDIMG}")
    }

    
    stage('Deploy Build') {
        def deployApp = "docker run -d --name test-build -p 8082:80 ${env.BUILDIMG}"
       sh label: '', script: "${deployApp}"
    }
}
