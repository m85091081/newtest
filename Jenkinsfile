#!/usr/bin/env groovy
// Groovy Language

def sendBuildStatus(status, message) {
  step([
    $class: 'GitHubCommitStatusSetter',
    contextSource: [
      $class: 'ManuallyEnteredCommitContextSource',
      context: 'JenkinsStaging'
    ],
    statusResultSource: [
      $class: 'ConditionalStatusResultSource',
      results: [[
        $class: 'AnyBuildResult',
        message: message,
        state: status
      ]]
    ]
  ])
}


if (env.CHANGE_ID != null) {
  node {
  checkout scm
  echo "pr"
  echo "Deployed to production"
  }
} else {
  node {
  checkout scm
  echo "not pr"
  }
}

