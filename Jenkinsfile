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
                /*sh "helm repo add stable https://kubernetes-charts.storage.googleapis.com"*/
                //sh "helm repo add chartmuseum http://chartrepo.172.10.3.50.nip.io:31073"
                //sh "helm repo list"
                /*sh "helm search repo"*/
                /*sh "helm install nginx-test stable/nginx-ingress"*/
                /*sh "helm uninstall nginx-test -n ns-jenkins"*/
                }
        }

        stage('Run kubectl') {
            container('kubectl') {
                kubeconfig(caCertificate: 'LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUN5RENDQWJDZ0F3SUJBZ0lCQURBTkJna3Foa2lHOXcwQkFRc0ZBREFWTVJNd0VRWURWUVFERXdwcmRXSmwKY201bGRHVnpNQjRYRFRJd01EY3dNakExTWpZeU1sb1hEVE13TURZek1EQTFNall5TWxvd0ZURVRNQkVHQTFVRQpBeE1LYTNWaVpYSnVaWFJsY3pDQ0FTSXdEUVlKS29aSWh2Y05BUUVCQlFBRGdnRVBBRENDQVFvQ2dnRUJBSzZuCjdsTHZacEsvVzVmb3g4TGYvd1VpdlFZMzdpRGM4UkJOaThyZERSZDEwWVUwdlpyaEltL2NTdjlaM3d5R2g2WUEKT29wZEZqUzE3c1V3ZWhoZTNiUG5yYjZlNDVHYVBCSGM0Wjk3RFdsSmZpK2NRNHN1SWhmNFM5bmIraWxTZ1owUwpLd3BwWGI5ZUMybHJrcElOTzgwTEI4WDlTL3Rmemk1Mi9aUndrY2lteWFjdENFVHVEbXNqN21sN2N6TWZnY0RHCk5CSmRMNVJpanBLYUZoRHFXSU9QOE1nellETi9JdXB3WU5KK3ZyZTZUWUs0SWZIY3ZOYVZ0aUl4Y3dNNXBKRFoKTnlLc2MwYVhkYk5UTlBiZlkzMnpmc3o5NUlkUHpPYmFsL3dMcEk0a2lpV1dPQU1tVVo1RW1JUmo0bFhuSTdHZApjWWFJS0hJMzJqblB2VmtLa0NzQ0F3RUFBYU1qTUNFd0RnWURWUjBQQVFIL0JBUURBZ0trTUE4R0ExVWRFd0VCCi93UUZNQU1CQWY4d0RRWUpLb1pJaHZjTkFRRUxCUUFEZ2dFQkFLMnIwYTc1ZG44K3NaVU0vOUpFT1RQOXIyUDYKamhPdWIzQUtoRkhTS25teW5aRmM3QTgySkFEMGhUWElXN3ZQVXFjZmowbGFHdURCcWw3V0k0RCtseTdlV2xMcgo3b1RUUkZFTGNYM0crSm9HNDFtR2NPd3A5c3pESm4xOHkxakpuR2xuS05FS2JIY3ptRXNlMzdveDhFdEZDcHVUCktEdnRaK0U0ZDlxQ2Y5S0laZy9aYVlsdjEveGZZR3FrSElsMWpCbVVhTGFrSXkxQk1yQVZleitHOUptZEdxVUUKcEJ2Y0xNN0tiR3h2RC9NQXhtL3hiU0xiRUpjQWphdXEwRm9RUUVoRy9NemV3dVIxOHV0UFBwN0p0L2FxYnVLLwpuVnoxN3NEVkFtM2NSSmp6Wm90NnVTYm1mOE5PNlg1SWJnREVQWnpRWE8zdm9HeVcybTRGY3VXTCtoZz0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo=', credentialsId: '716efe7e-c7d0-47b8-8c7f-5718d1ae03db', serverUrl: 'https://172.10.3.3:6443') 
                {
                   sh 'kubectl get pods'                 
                }
            }
        }
    }
}
