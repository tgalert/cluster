# EKS Cluster

Create EKS cluster and secrets.


## Usage

To fully initialise the cluster, you have to carry out the following steps.

### Create Cluster

    ~~~bash
    ./cluster.sh
    ~~~

### Create Secrets

We use Kubernetes [secrets](https://kubernetes.io/docs/concepts/configuration/secret/) to provide sensitive data (such as API keys) to the pods in the cluster. The following secrets exist:

- `telegram-creds`: Telegram API ID and hash to enable application to connect to the Telegram API
- `mailgun-creds`: Mailgun API key to enable application to send emails via Mailgun
- `rabbitmq-creds`: RabbitMQ credentials for each user of the system to enable the `tgalert` backend of each user to connect to RabbitMQ
    - The credentials for each user are contained in a single secret key/value pair
    - The key is the user ID
    - The value is a JSON string with the following format: `{"username":"xxx","password":"yyy","vhost":"zzz"}`

You have to substitute your own values in the `telegram-creds.yml` and `mailgun-creds.yml` secret files before creating the secrets. The data items of the `rabbitmq-creds` secrets will be automatically added when a user is created.

To create all the secrets at once, use the following command:

~~~bash
kubectl apply -f secrets/
~~~

