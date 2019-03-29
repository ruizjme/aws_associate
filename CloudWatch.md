# CloudWatch

For performance monitoring. Not to be confused with CloudTrail (auditing).

Basic monitoring: every 5 min. Free.
Detailed monitoring: every 1 min. Costs money.

## Dashboards

Default metrics available for EC2:
* CPU
* Disk
* Network
* Status

## Alarms

Notifications can be sent for certain metrics if they go over an arbitrary value.

## Events

When things change state, events can trigger other actions.

## Logs

Logs (from aws and from third parties) can be aggregated and monitored here. Agent to be installed in EC2 instance.

## Metrics

Single metric monitoring (same as dashboards but one by one).
