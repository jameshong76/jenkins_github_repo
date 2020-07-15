@Library('my-shared-library')
import com.foo.utils.PodTemplates

slaveTemplates = new PodTemplates()

slaveTemplates.dockerTemplate {
    node('builder') {
      container('docker') {
        sh 'echo hello from docker'
      }
    }
}
