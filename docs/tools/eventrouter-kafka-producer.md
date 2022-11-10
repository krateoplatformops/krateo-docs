# Eventrouter Kafka Producer

> [EventRouter](https://github.com/krateoplatformops/eventrouter) consumer microservice dispatching cloudevents to Kafka.

It expose two endpoints:

- `/healthz` - health check endpoint (GET)
- `/handle` - eventrouter hook endpoint (POST)

## How to install

```sh
$ helm repo add krateo https://charts.krateo.io
$ helm repo update krateo
$ helm install eventrouter-kafka-producer krateo/eventrouter-kafka-producer --namespace krateo-system --create-namespace
```

## Env Vars

| Name                               | Description                             | Default Value     |
|:-----------------------------------|:----------------------------------------|:------------------|
| EVENTROUTER_KAFKA_PRODUCER_PORT    | port to listen on                       | 8080              |
| EVENTROUTER_KAFKA_PRODUCER_DEBUG   | dump verbose output                     | false             |
| EVENTROUTER_KAFKA_PRODUCER_BROKERS | comma separated list of kafka brokers   | 127.0.0.1:9092    |
| EVENTROUTER_KAFKA_PRODUCER_TOPIC   | send events to this Kafka topic         | test-topic        |

## Registering with the EventRouter


To register this service with the [eventrouter](https://github.com/krateoplatformops/eventrouter) apply a manifest like this:

```yaml
cat <<EOF | kubectl apply -f -
apiVersion: eventrouter.krateo.io/v1alpha1
kind: Registration
metadata:
  name: kafka-producer-registration
spec:
  serviceName: Kafka Producer
  # Your custom hook service endpoint
  endpoint: https://this.service.addr:8080/handle
EOF
```

