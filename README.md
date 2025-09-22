# aws-training

### Training in AWS Services:

- ECR
- ECS

### Setup

- Crates image:

```
docker build -t webapi -f  src\AWSTraining.WebAPI\Dockerfile .
```

- Runs image:

```
docker run -d -p 5001:80 --name my-webapi webapi
```