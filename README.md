# EKS Cluster

CloudFormation template and launch script for the EKS cluster.

Additionally includes templates for the following Kubernetes resources:

- RabbitMQ application ([deployment](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.12/#deployment-v1-apps) and [service](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.12/#service-v1-core))
- [Secret](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.12/#secret-v1-core) consumed by other pods in the cluster
    - This template file is excluded from version control (see below)

## Usage

To fully initialise the cluster, you have to carry out the following steps.

### Create Cluster

    ~~~bash
    ./cluster.sh
    ~~~

### Create RabbitMQ Application

    ~~~bash
    kubectl apply -f rabbitmq.yml
    ~~~

### Create Secrets

We use Kubernetes [secrets](https://kubernetes.io/docs/concepts/configuration/secret/) to get sensitive data (such as API keys) into the cluster. The template file defining the secrets is excluded from version control, so you have to create it first.

Create the file `secrets.yml` with the following content:

~~~yaml
apiVersion: v1
kind: Secret
metadata:
  name: secrets
type: Opaque
stringData:
  TG_API_ID: [[REPLACE]]
  TG_API_HASH: [[REPLACE]]
  MAILGUN_API_KEY: [[REPLACE]]
~~~

Create the secret:

~~~bash
kubectl apply -f secrets.yml
~~~

These secrets will be read by other pods in the cluster.
