node {
  stage('check environment'){
    echo sh(returnStdout: true, script: 'env')
  }
  stage('check git'){
    echo "Git status: "
    echo sh(returnStdout: true, script: 'cd /tmp/build && git status')
    
    def gitCommitId = sh(returnStdout: true, script: 'cd /tmp/build && git rev-parse HEAD')
    echo gitCommitId
    
    GIT_SHORT_COMMIT = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%h'").trim()
    echo "Git short commit: "
    echo GIT_SHORT_COMMIT
  }
  stage('buildImage'){
    openshiftBuild(buildConfig: 'build-puppetserver-code', showBuildLogs: 'true')
  }
  stage('deployApplication'){
    openshiftDeploy(deploymentConfig: 'puppetserver-code')
  }
}
