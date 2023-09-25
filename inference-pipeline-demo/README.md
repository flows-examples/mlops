# Inference Pipeline Demo

To run it, [build the image](../inference-pipeline-demo/) and run it locally:

```shell
docker run -it --rm -p 8080:8080 -v <your path>/flows-examples/mlops/inference-pipeline-demo:/home/kogito/serverless-workflow-project/src/main/resources quay.io/<your namespace>/sonataflow-python-devmode:latest
```

Then you can test with:

```shell
curl -X 'POST' \
  'http://localhost:8080/pipeline' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{ "image": "src/main/resources/images/coco_image.jpg" }'
```

## Deploy on Kubernetes

To deploy it on Kubernetes, you should install the [SonataFlow Operator](https://sonataflow.org/serverlessworkflow/latest/cloud/operator/install-serverless-operator.html), and then deploy the service:

```shell
kubectl kustomize inference-pipeline-demo/ | kubectl apply -n <namespace> -f -
```
