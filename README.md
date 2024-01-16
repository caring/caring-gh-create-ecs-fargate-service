# Provision ECS Service

## Description

This GitHub Action provisions an Amazon ECS service. It first attempts to update an existing service. If the service does not exist, it creates a new one. The action ensures that the specified ECS service is associated with the provided task definition, target group, subnets, security groups, and ECS cluster.

## Inputs

| Name                  | Description                                                  | Required | Default                  |
| --------------------- | ------------------------------------------------------------ | -------- | ------------------------ |
| `ecsServiceName`      | The name of the ECS service.                                | ✔        |                          |
| `taskDefArn`          | The ARN of the task definition.                              | ✔        |                          |
| `targetGroupArn`      | The ARN of the target group.                                 | ✔        |                          |
| `subnetIds`           | The IDs of the subnets.                                      | ✔        |                          |
| `securityGroups`      | The IDs of the security groups.                              | ✔        |                          |
| `ecsClusterArn`       | The ARN of the ECS cluster.                                  | ✔        |                          |
| `containerName`       | The name of the container.                                   | ✔        |                          |
| `containerPort`       | The port of the container.                                   | ✖        | `3000`                   |

## Example Usage

```yaml
jobs:
  provision-ecs-service:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Provision ECS Service
        id: ecs-service
        uses: caring/gh-create-ecs-fargate-service@v1.0.0
        with:
          ecsServiceName: 'my_service'
          taskDefArn: 'arn:aws:ecs:us-east-1:123456789012:task-definition/my-task:1'
          targetGroupArn: 'arn:aws:elasticloadbalancing:us-east-1:123456789012:targetgroup/my-targets/73e2d6bc24d8a067'
          subnetIds: 'subnet-0e4a7ab5addd5b076,subnet-0a2b3c4d5e6f7g8h9'
          securityGroups: 'sg-0e2e6b4643b14a779,sg-0a1b2c3d4e5f6g7h8'
          ecsClusterArn: 'arn:aws:ecs:us-east-1:123456789012:cluster/my-cluster'
          containerName: 'my_container'
          containerPort: '8080'
```

## License

This project is licensed under the MIT License.

## Author

Written by the DevOps Team.