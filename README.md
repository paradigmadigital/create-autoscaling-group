# create-autoscaling-group

Create autoscaling group from launch configuration

# Role Variables

* `region`                            : Region to launch the ec2 instance to create the new AMI
* `availability_zones`                : List of availability zone names in which to create the group.  Defaults to all the availability zones in the region if vpc_zone_identifier is not set.
* `lc_name`                           : Name of the launch configuration
* `asg_name`                          : Auto Scaling Group name
* `asg_min_size`                      : Minimum number of instances in group, if unspecified then the current group value will be used.
* `asg_max_size`                      : Maximum number of instances in group, if unspecified then the current group value will be used.
* `asg_vpc`                           : List of VPC subnets to use
* `asg_default_cooldown`              : The number of seconds after a scaling activity completes before another can begin.  [Default: 300 seconds]
* `asg_health_check_type`             : The service you want the health status from, Amazon EC2 or Elastic Load Balancer. (Choices: EC2, ELB)[Default : EC2]
* `asg_health_check_period`           : Length of time in seconds after a new EC2 instance comes into service that Auto Scaling starts checking its health.  [Default: 500 seconds]
* `asg_desired_capacity`              : Desired number of instances in group, if unspecified then the current group value will be used. [Default: (null)]
* `scaling_policy_scaling_adjustment` : The amount by which the autoscaling group is adjusted by the policy [Default: (null)]
* `scaling_policy_cooldown`           : The minimum period of time between which autoscaling actions can take place [Default: (null)]
* `metric_scaleup_threshold`          : Sets the min/max bound for triggering the alarm [Default: (null)]
* `metric_alarm_period`               : The time (in seconds) between metric evaluations [Default: (null)]
* `metric_alarm_evaluation_periods`   : The number of times in which the metric is evaluated before final calculation [Default: (null)]

# Example playbook

```yaml
- hosts: localhost
  connection: local
  gather_facts: no
  roles:
    - create-autoscaling-group
```

# License

GPLv2

# Author Information
jamatute (jamatute@paradigma)
