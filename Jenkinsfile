/* pipeline 변수 설정 */
def DOCKER_IMAGE_NAME = "abasya/project-repo"           // 생성하는 Docker image 이름
def DOCKER_IMAGE_TAGS = "batch-visualizer-auth"  // 생성하는 Docker image 태그
def NAMESPACE = "hong"
//def NAMESPACE = "ns-project"
def VERSION = "${env.BUILD_NUMBER}"
def DATE = new Date();

podTemplate(label: 'builder',
            containers: [
                containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.15.3', command: 'cat', ttyEnabled: true),
                containerTemplate(name: "helm", image: "lachlanevenson/k8s-helm:latest", ttyEnabled: true, command: "cat")
            ]) {
    node('builder') {
        stage('Checkout') {
             checkout scm   // gitlab으로부터 소스 다운
        }

        stage( "Deploy to cluster" ) {
            container("helm") {
                echo "Install with chart file !"
                /*sh "helm install uangel-smsf /root/jenkins/auth/dish-smsf -n smsf"*/
                /*sh "helm list -n smsf"
                sh "helm repo add stable https://kubernetes-charts.storage.googleapis.com"*/
                //sh "helm repo add chartmuseum http://chartrepo.172.10.3.50.nip.io:31073"
                //sh "helm repo list"
                /*sh "helm search repo"*/
                /*sh "helm install nginx-test stable/nginx-ingress"*/
                /*sh "helm uninstall nginx-test -n ns-jenkins"*/
                }
        }

        stage('Run kubectl') {
            container('kubectl') {
                withCredentials([usernamePassword(
                    credentialsId: 'kuber_credential',
                    usernameVariable: 'USERNAME',
                    passwordVariable: 'PASSWORD')]) {
                        /* namespace 존재여부 확인. 미존재시 namespace 생성 */
                        sh "kubectl get ns ${NAMESPACE}|| kubectl create ns ${NAMESPACE}"

                        /* yaml파일로 배포를 수행한다 */
                        sh "kubectl get all --all-namespaces"
                }
            }
        }
    }
}
