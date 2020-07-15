package com.foo.utils

public void dockerTemplate(body) {
  podTemplate(
        containers: [containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true)],
        volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')]) {
    body.call()
}
}

public void mavenTemplate(body) {
  podTemplate(
        containers: [containerTemplate(name: 'maven', image: 'maven', command: 'cat', ttyEnabled: true)],
        volumes: [secretVolume(secretName: 'maven-settings', mountPath: '/root/.m2'),
                  persistentVolumeClaim(claimName: 'maven-local-repo', mountPath: '/root/.m2nrepo')]) {
    body.call()
}
}

return this

import com.foo.utils.podTemplates

slaveTemplates = new podTemplates()

slaveTemplates.dockerTemplate {
  slaveTemplates.mavenTemplate {
    node(POD_LABEL) {
      container('docker') {
        sh 'echo hello from docker'
      }
      container('maven') {
        sh 'echo hello from maven'
      }
     }
  }
}
