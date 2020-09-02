你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
# AWS Container Day sample API Service in Go
# eks-workshop-sample-api-service-go

A sample Kubernetes service used in the AWS Container Day CI/CD Pipeline module.

The Dockerfile is a [multi-stage](https://docs.docker.com/develop/develop-images/multistage-build/) build that
compiles the Go application and then packages it in a minimal image that pulls from [scratch](https://hub.docker.com/_/scratch/).
The size of this Docker image is ~ 3.2 MiB.

The buildspec.yml file is used by the [AWS CodeBuild](https://aws.amazon.com/codebuild/) stage. In this file, it pulls down
kubectl, builds the container image, pushes the image to [Amazon ECR](https://aws.amazon.com/ecr/) and then deploys the change to the
[Amazon EKS Cluster](https://aws.amazon.com/eks/).

In the hello-k8s.yml file, you will find the Kubernetes [service](https://kubernetes.io/docs/concepts/services-networking/service/) and
[deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) definitions. The service is configured with
a [LoadBalancer](https://kubernetes.io/docs/tasks/access-application-cluster/create-external-load-balancer/) which prompts Kubernetes
to launch an external load balancer using an [AWS ELB](https://aws.amazon.com/elasticloadbalancing/).
