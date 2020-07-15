@Library('my-shared-library')
import com.foo.utils.PodTemplates

slaveTemplates = new PodTemplates()

slaveTemplates.dockerTemplate {
  slaveTemplates.mavenTemplate {
    node('builder') {
      container('docker') {
        sh 'echo hello from docker'
      }
      /*container('maven') {
        sh 'echo hello from maven'
      }*/
     }
  }
}
