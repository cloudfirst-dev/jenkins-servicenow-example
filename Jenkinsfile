import groovy.json.JsonSlurper

node('nodejs') {
  stage 'build'
  openshiftBuild(buildConfig: 'servicenow-example', showBuildLogs: 'true')

  stage 'request RFC before deployment'
  def response = serviceNow_createChange serviceNowConfiguration: [instance: 'dev59729', producerId: '563504cc47410200e90d87e8dee490e2'], credentialsId: 'servicenow'
  def createResponse = jsonSlurper.parseText(response.content)
  def sysId = createResponse.result.sys_id
  def changeNumber = createResponse.result.number
  println "change number ${changeNumber} created"

  // get current state of change
  def response = serviceNow_UpdateChangeItem serviceNowConfiguration: [instance: 'dev59729'], credentialsId: 'servicenow', serviceNowItem: [sysId: sysId]
  echo response 

  stage 'deploy'
  openshiftDeploy(deploymentConfig: 'servicenow-example')
}