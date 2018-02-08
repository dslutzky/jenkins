node("docker") {
    docker.withRegistry('dansl1982',
'docker-hub') {
    
        git url: "https://github.com/dslutzky/jenkins.git", credentialsId: 'git'
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "jenkins"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
