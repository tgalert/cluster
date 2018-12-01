# EKS Cluster

CloudFormation template and launch script for the EKS cluster.

Also includes the RabbitMQ application that runs on the cluster.

## Usage

1. Create cluster:
    ~~~bash
    ./cluster.sh
    ~~~
2. Create RabbitMQ application in cluster:
    ~~~bash
    kubectl apply -f rabbitmq.yml
    ~~~
