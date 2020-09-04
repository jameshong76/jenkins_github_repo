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
                containerTemplate(name: "helm", image: "lachlanevenson/k8s-helm:latest", ttyEnabled: true, command: "cat"),
                containerTemplate(name: 'newman', image: 'postman/newman', ttyEnabled: true, command: 'cat')
            ]) {
    node('builder') {
        stage('Checkout') {
             checkout scm   // gitlab으로부터 소스 다운
        }

        stage( "Deploy to cluster" ) {
            container("helm") {
                //def props = readProperties  file:'/var/jenkins_home/jobs/pipe/builds/test.properties'
                //def Var1= props['Monday']
                //echo "Var1=${Var1}"
                echo "Install with chart file !"             
                /*sh "helm install uangel-smsf /root/jenkins/auth/dish-smsf -n smsf"*/
                /*sh "helm list -n smsf"
                /*sh "helm repo add stable https://kubernetes-charts.storage.googleapis.com"*/
                //sh "helm repo add chartmuseum http://chartrepo.172.10.3.50.nip.io:31073"
                //sh "helm repo list"
                /*sh "helm search repo"*/
                /*sh "helm install nginx-test stable/nginx-ingress"*/
                /*sh "helm uninstall nginx-test -n ns-jenkins"*/
                }
        }
failure!!!!!
        stage('Run kubectl') {
            container('kubectl') {
                withKubeConfig([credentialsId: 'a5f64e94-caaa-4f8e-8982-faadac0652f9', serverUrl: 'https://172.10.3.86:6443']){
                        sh "kubectl get pod"
                }
            }
        }
               
    }
}
