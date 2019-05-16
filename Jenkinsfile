node('nodejs') {
  stage 'build'
  openshiftBuild(buildConfig: 'servicenow-ex', showBuildLogs: 'true')
  stage 'deploy'
  openshiftDeploy(deploymentConfig: 'servicenow-ex')
}