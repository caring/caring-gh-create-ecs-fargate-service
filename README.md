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

This action will provision an ECS service for the specified ECS cluster, associated with the provided task definition, target group, subnets, and security groups. It can be used in your workflow to ensure proper deployment and management of your ECS services.

## License

This project is licensed under the MIT License.

## Author

Written by the DevOps Team.