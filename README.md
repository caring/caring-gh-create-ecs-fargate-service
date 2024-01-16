# Provision ECS Service Action

This GitHub action provisions an Amazon ECS service. It first attempts to update an existing service. If the service does not exist, it creates a new one.

## Inputs

| Input | Description | Required | Default |
| ----- | ----------- | -------- | ------- |
| `ecsServiceName` | The name of the ECS service. | Yes | N/A |
| `taskDefArn` | The ARN of the task definition. | Yes | N/A |
| `targetGroupArn` | The ARN of the target group. | Yes | N/A |
| `subnetIds` | The IDs of the subnets. | Yes | N/A |
| `securityGroups` | The IDs of the security groups. | Yes | N/A |
| `ecsClusterArn` | The ARN of the ECS cluster. | Yes | N/A |
| `containerName` | The name of the container. | Yes | N/A |
| `containerPort` | The port of the container. | No | `3000` |

## Usage

You can use this action in your workflow file as follows:

```yaml
- name: Provision ECS Service
    uses: ./
    with:
        ecsServiceName: 'my_service'
        taskDefArn: 'arn:aws:ecs:us-east-1:123456789012:task-definition/my-task:1'
        targetGroupArn: 'arn:aws:elasticloadbalancing:us-east-1:123456789012:targetgroup/my-targets/73e2d6bc24d8a067'
        subnetIds: 'subnet-0e4a7ab5addd5b076,subnet-0a2b3c4d5e6f7g8h9'
        securityGroups: 'sg-0e2e6b4643b14a779,sg-0a1b2c3d4e5f6g7h8'
        ecsClusterArn: 'arn:aws:ecs:us-east-1:123456789012:cluster/my-cluster'
        containerName: 'my_container'
        containerPort: '8080'