# EKS Cluster and RabbitMQ

CloudFormation template and launch script for the EKS cluster, plus RabbitMQ application running on the cluster.

## Usage

1. Create cluster
    ~~~bash
    ./cluster.sh
    ~~~
2. Create RabbitMQ application in cluster
    ~~~bash
    kubectl apply -f rabbitmq.yml
    ~~~
