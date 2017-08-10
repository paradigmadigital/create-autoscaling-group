# create-autoscaling-group

Create autoscaling group from launch configuration

## Role Variables

* `region`                      : Region to launch the ec2 instance to create the new AMI
* `availability_zones`          : List of availability zone names in which to create the group.  Defaults to all the availability zones in the region if vpc_zone_identifier is not set.

* `lc.name`                     : Name of the launch configuration

* `asg.name`                    : Auto Scaling Group name
* `asg.min_size`                : Minimum number of instances in group, if unspecified then the current group value will be used.
* `asg.max_size`                : Maximum number of instances in group, if unspecified then the current group value will be used.
* `asg.vpc`                     : List of VPC subnets to use
* `asg.load_balancers`          : List of ELB names to use for the group [Default: (null)]
* `asg.default_cooldown`        : The number of seconds after a scaling activity completes before another can begin.  [Default: 300 seconds]
* `asg.health_check_type`       : The service you want the health status from, Amazon EC2 or Elastic Load Balancer. (Choices: EC2, ELB)[Default: EC2]
* `asg.health_check_period`     : Length of time in seconds after a new EC2 instance comes into service that Auto Scaling starts checking its health.  [Default: 500 seconds]
* `asg.desired_capacity`        : Desired number of instances in group, if unspecified then the current group value will be used. [Default: (null)]
* `asg.tags`                    : A list of tags to add to the Auto Scale Group. Optional key is 'propagate_at_launch', which defaults to true.  [Default: None]

* `sp.increase_adjustment_type` : The type of change in capacity of the increasing of the autoscaling group (Choices: ChangeInCapacity, ExactCapacity, PercentChangeInCapacity)[Default: (null)]
* `sp.decrease_adjustment_type` : The type of change in capacity of the decreasing of the autoscaling group (Choices: ChangeInCapacity, ExactCapacity, PercentChangeInCapacity)[Default: (null)]
* `sp.increase_adjustment`      : The amount by which the autoscaling group is increased by the scaling policy [Default: (null)]
* `sp.decrease_adjustment`      : The amount by which the autoscaling group is increased by the scaling policy [Default: (null)]
* `sp.increase.cooldown`        : The minimum period of time between which autoscaling increase actions can take place [Default: (null)]
* `sp.decrease.cooldown`        : The minimum period of time between which autoscaling decrease actions can take place [Default: (null)]

* `metric.scaleup.threshold`    : Sets the max bound for triggering the scale up alarm [Default: (null)]
* `metric.scaleup.alarm.period` : The time (in seconds) between metric evaluations for the scale up alarm [Default: (null)]
* `metric.scaleup.alarm.evaluation_periods`   : The number of times in which the metric is evaluated before final calculation for the scale up alarm [Default: (null)]
* `metric.scaledown.threshold`  : Sets the min bound for triggering the scale down alarm [Default: (null)]
* `metric.scaledown.alarm.period`             : The time (in seconds) between metric evaluations for the scale down alarm [Default: (null)]
* `metric.scaledown.alarm.evaluation_periods` : The number of times in which the metric is evaluated before final calculation for the scale up alarm [Default: (null)]
* `metric.namespace`                 : Which namespace you want the alarm to use.


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
