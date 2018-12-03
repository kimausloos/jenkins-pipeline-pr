node {
  stage('check environment'){
    echo sh(returnStdout: true, script: 'env')
  }
  stage('buildImage'){
    openshiftBuild(buildConfig: 'build-puppetserver-code', showBuildLogs: 'true')
  }
  stage('deployApplication'){
    openshiftDeploy(deploymentConfig: 'puppetserver-code')
  }
}
