node('nodejs') {
  stage 'build'
  openshiftBuild(buildConfig: 'servicenow-example', showBuildLogs: 'true')
  stage 'deploy'
  openshiftDeploy(deploymentConfig: 'servicenow-example')
}