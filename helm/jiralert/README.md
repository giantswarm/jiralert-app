# jiralert

Alertmanager plugin that creates Jira tickets

**Homepage:** <https://github.com/giantswarm/jiralert-app>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| name | string | `"jiralert"` |  |
| serviceType | string | `"managed"` |  |
| global.podSecurityStandards.enforced | bool | `false` |  |
| project.branch | string | `"[[ .Branch ]]"` |  |
| project.commit | string | `"[[ .SHA ]]"` |  |
| image.registry | string | `"gsoci.azurecr.io"` |  |
| image.name | string | `"giantswarm/jiralert"` |  |
| image.tag | string | `"1.2-extra-functions"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| init.registry | string | `"gsoci.azurecr.io"` |  |
| init.name | string | `"giantswarm/busybox"` |  |
| init.tag | string | `"1.34.1"` |  |
| pod.user.id | int | `1000` |  |
| pod.group.id | int | `1000` |  |
| psp.enabled | bool | `true` |  |
| networkPolicy.enabled | bool | `true` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| initResources.requests.cpu | string | `"100m"` |  |
| initResources.requests.memory | string | `"220Mi"` |  |
| initResources.limits.cpu | string | `"100m"` |  |
| initResources.limits.memory | string | `"220Mi"` |  |
| resources.requests.cpu | string | `"100m"` |  |
| resources.requests.memory | string | `"220Mi"` |  |
| resources.limits.cpu | string | `"100m"` |  |
| resources.limits.memory | string | `"220Mi"` |  |
| securityContext.allowPrivilegeEscalation | bool | `false` |  |
| securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| securityContext.privileged | bool | `false` |  |
| securityContext.runAsNonRoot | bool | `true` |  |
| securityContext.readOnlyRootFilesystem | bool | `true` |  |
| template | string | `""` |  |
| jiralert.credentials | object | `{}` |  |
| jiralert.config.api_url | string | `"https://example.atlassian.net/"` |  |
| jiralert.config.issue_type | string | `"Task"` |  |
| jiralert.config.issue_priority | string | `""` |  |
| jiralert.config.reopen_state | string | `"To Do"` |  |
| jiralert.config.resolution | string | `"Won't Fix"` |  |
| jiralert.config.reopen_duration | string | `""` |  |
| jiralert.receivers | list | `[]` |  |
