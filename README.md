# create-autoscaling-group

Create autoscaling group from launch configuration

## Role Variables

* `region`                      : Region to launch the ec2 instance to create the new AMI
* `availability_zones`          : List of availability zone names in which to create the group.  Defaults to all the availability zones in the region if vpc_zone_identifier is not set.

* `lc.name`                     : Name of the launch configuration

* `asg.name`                : Auto Scaling Group name
* `asg.min_size`            : Minimum number of instances in group, if unspecified then the current group value will be used.
* `asg.max_size`            : Maximum number of instances in group, if unspecified then the current group value will be used.
* `asg.vpc`                 : List of VPC subnets to use
* `asg.load_balancers`      : List of ELB names to use for the group
* `asg.default_cooldown`    : The number of seconds after a scaling activity completes before another can begin.
* `asg.health_check_type`   : The service you want the health status from, Amazon EC2 or Elastic Load Balancer. (Choices: EC2, ELB)
* `asg.health_check_period` : Length of time in seconds after a new EC2 instance comes into service that Auto Scaling starts checking its health.
* `asg.desired_capacity`    : Desired number of instances in group, if unspecified then the current group value will be used.
* `asg.tags`                : A list of tags to add to the Auto Scale Group. Optional key is 'propagate_at_launch', which defaults to true.

* `metrics.policy`                     : This name may be whatever you want. It won't be used in the playbooks.
* `metrics.policy.policy_name         `: Policy name.
* `metrics.policy.metric_name         `: Metric name.
* `metrics.policy.adjustment_type     `: The type of change in capacity of the autoscaling group [Choices: ChangeInCapacity, ExactCapacity and PercentChangeInCapacity]
* `metrics.policy.scaling_adjustment  `: The amount by which the autoscaling group is adjusted by the policy.
* `metrics.policy.min_adjustment_step `: Minimum amount of adjustment when policy is triggered.
* `metrics.policy.cooldown            `: Time to wait until next autoscaling action.
* `metrics.policy.type                `: Metric type [Choices: CPUUtilization, Latency, etc].
* `metrics.policy.namespace           `: Namespace of the matric. [Choices: AWS/EC2, AWS/ELB, etc]
* `metrics.policy.statistic           `: How to count the metric. [Choices: Average, Sum, Max, etc]
* `metrics.policy.threshold           `: The bound for triggering the alarm.
* `metrics.policy.comparison          `: The comparison symbol. It would be: $type $comparison $threshold.
* `metrics.policy.period              `: The time (in seconds) between metric evaluations.
* `metrics.policy.evaluation_periods  `: The number of times in which the metric is evaluated before final calculation.
* `metrics.policy.unit                `: The threshold's unit of measurement [Choices: Seconds, Bytes, etc].
* `metrics.policy.increase_adjustment_type` : The type of change in capacity of the increasing of the autoscaling group (Choices: ChangeInCapacity, ExactCapacity, PercentChangeInCapacity)

## Example playbook

```yaml
- hosts: localhost
  connection: local
  gather_facts: no
  roles:
    - create-autoscaling-group
```

## License

GPLv2

## Author Information
jamatute (jamatute@paradigma)
