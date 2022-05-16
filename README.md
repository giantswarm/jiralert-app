[![CircleCI](https://circleci.com/gh/giantswarm/jiralert-app.svg?style=shield)](https://circleci.com/gh/giantswarm/jiralert-app)

# Jiralert chart

Giant Swarm offers a [Jiralert](https://github.com/prometheus-community/jiralert/) App which can be installed in workload clusters.
Here we define the jiralert-app chart with its templates and default configuration.

Jiralert is an [Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/) plugin that uses receivers to create Jira tickets in the configured projects.

## Installing

There are several ways to install this app onto a workload cluster.

- [Using our web interface](https://docs.giantswarm.io/ui-api/web/app-platform/#installing-an-app).
- By creating an [App resource](https://docs.giantswarm.io/ui-api/management-api/crd/apps.application.giantswarm.io/) in the management cluster as explained in [Getting started with App Platform](https://docs.giantswarm.io/app-platform/getting-started/).

## Configuring

### values.yaml

**This is an example of a values file you could upload using our web interface.**

```yaml
template: |
    {{ define "jira.summary" }}Jira summary template{{ end }}
    
    {{ define "jira.description" }}Jira description template{{ end }}

jiralert:
  config:
      # API access url
      api_url: "https://your_jira_instance.atlassian.net/"
      # The type of JIRA issue to create. Required.
      issue_type: "Task"
      # Issue priority. Optional.
      issue_priority: "Critical"
      # State to transition into when reopening a closed issue. Required.
      reopen_state: "To Do"
      # Do not reopen issues with this resolution. Optional.
      resolution: "Won't Fix"
      # Amount of time after being closed that an issue should be reopened, after which, a new issue is created. Optional (default: always reopen)
      reopen_duration: "0h"
  receivers: 
    # Set one or more receivers
    # Find another example in https://github.com/prometheus-community/jiralert/blob/master/examples/jiralert.yml

      # Name must match the Alertmanager receiver name. Required.
    - name: 'jiralert-receiver'
      # JIRA project to create the issue in. Required.
      project: JIR
      # Copy all Prometheus labels into separate JIRA labels. Optional (default: false).
      add_group_labels: true
      # Standard or custom field values to set on created issue. Optional.
      fields:
        # TextField
        customfield_10001: "Random text"
        # SelectList
        customfield_10002: {"value": "red"}
        # MultiSelect
        customfield_10003: [{"value": "red"}, {"value": "blue"}, {"value": "green"}]
  credentials:
    # You can set the credentials here or bring your own jiralert-credentials secret
    jira_username: "EXAMPLE_USERNAME"
    jira_password: "P@$$w0rd!"
```

See our [full reference on how to configure apps](https://docs.giantswarm.io/app-platform/app-configuration/) for more details.

## Sample Alertmanager rule

**This is an example of an Alertmanager rule to be used with the jiralert App**

```yaml
alertmanager:
  config:
    route:
      routes:
      - match:
          alertname: ExampleRule
        receiver: 'jiralert-receiver'
        group_by: ['namespace']
    receivers:
    - name: 'jiralert-receiver'
      webhook_configs:
      - url: 'http://jiralert:9097/alert'
        send_resolved: false
additionalPrometheusRulesMap: 
  example-rules:
    groups:
    - name: example-rule-group
      rules:
      - alert: ExampleRule 
        expr: example_metrics{namespace="default"}
        annotations:
          summary: "New alert for {{ $labels.namespace }}"
          description: "An alertmanager alert was triggered for namespace: {{ $labels.namespace }}"
```

See [Prometheus alerting rules reference](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/) for more details.

## Credit

- https://github.com/prometheus-community/jiralert/
