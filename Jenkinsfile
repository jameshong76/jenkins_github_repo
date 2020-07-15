@Library('my-shared-library')
import com.foo.utils.PodTemplates

slaveTemplates = new PodTemplates()

slaveTemplates.mavenTemplate {
    node('builder') {
      container('maven') {
        sh 'echo hello from maven'
      }
    }
}
