---
title: Troubleshooting Workload Protection
aliases:
  - /security_platform/cloud_workload_security/troubleshooting/
  - /security_platform/cloud_security_management/troubleshooting/
further_reading:
- link: "/security/cloud_security_management/troubleshooting/vulnerabilities"
  tag: "Documentation"
  text: "Troubleshooting Cloud Security Vulnerabilities"
---

If you experience issues with Workload Protection, use the following troubleshooting guidelines. If you need further assistance, contact [Datadog support][1].

## Security Agent flare

Similar to the [Agent flare][1], you can send necessary troubleshooting information to the Datadog support team with one flare command.

The flare asks for confirmation before upload, so you may review the content before the Security Agent sends it.

In the commands below, replace `<CASE_ID>` with your Datadog support case ID if you have one, then enter the email address associated with it.

If you don't have a case ID, just enter your email address used to login in Datadog to create a new support case.

| Platform     | Command                                                                             |
| --------     | -------                                                                             |
| Docker       | `docker exec -it datadog-agent security-agent flare <CASE_ID>`                      |
| Kubernetes   | `kubectl exec -it <POD_NAME> -c security-agent -- security-agent flare <CASE_ID>`   |
| Host         | `sudo /opt/datadog-agent/embedded/bin/security-agent flare <CASE_ID>`               |

## Agent Self tests

In order to ensure that the communication between the `security-agent` and the `system-probe` is working as expected and that Workload Protection is able to detect system events, you can manually trigger self tests by running the following command:

| Platform     | Command                                                                             |
| --------     | -------                                                                             |
| Docker       | `docker exec -it datadog-agent security-agent runtime self-test`                    |
| Kubernetes   | `kubectl exec -it <POD_NAME> -c security-agent -- security-agent runtime self-test` |
| Host         | `sudo /opt/datadog-agent/embedded/bin/security-agent runtime self-test`             |

The self-test procedure creates some temporary files and rules to monitor them, and then triggers those rules to ensure that events are correctly propagated.

The following response appears when rules are propagated.
```
Runtime self test: OK
```

You can now see events coming from the `runtime-security-agent` in the Log Explorer.

{{< img src="security/cws/self_test_logs.png" alt="Self test events in the Log Explorer" style="width:90%;">}}

## Compatibility with custom Kubernetes network plugins

The network based detections of Workload Protection rely on the traffic control sub-system of the Linux kernel. This sub-system is known to introduce race conditions if multiple vendors try to insert, replace, or delete filters on the "clsact" ingress qdisc. Follow the checklist below to ensure that Workload Protection is properly configured:

* Check if your vendor leverages eBPF traffic control classifiers. If they do not, you can ignore this paragraph.
* Check if your vendor returns TC_ACT_OK or TC_ACT_UNSPEC after granting access to a network packet. If they return TC_ACT_UNSPEC, you can ignore this paragraph.
* Check which priority your vendor attaches their eBPF classifiers to:
  * If they use priority 1, Workload Protection network detections do not work inside your containers.
  * If they use priority 2 to 10, make sure to configure `runtime_security_config.network.classifier_priority` to a number strictly below the priority chosen by your vendor.
  * If they use priority 11 or higher, you can ignore this paragraph.

For example, there is a known race with Cilium 1.9 and lower with the Datadog Agent (version 7.36 to 7.39.1, 7.39.2 excluded) that may happen when a new pod is started. The race can lead to loss of connectivity inside the pod, depending on how Cilium is configured.

Ultimately, if the Datadog Agent or your third party vendors cannot be configured to prevent the issue from happening, you should disable the network based detections of Workload Protection by following the steps below:

* Add the following parameter to your `system-probe.yaml` configuration file on host based installations:
```yaml
runtime_security_config:
  network:
    enabled: false
```
* Add the following values if you're using the public Helm Chart to deploy the Datadog Agent:
```yaml
datadog:
  securityAgent:
    runtime:
      network:
        enabled: false
```
* Add the following environment variable if you're deploying the Datadog Agent container manually:
```bash
DD_RUNTIME_SECURITY_CONFIG_NETWORK_ENABLED=false
```
## Disable Workload Protection

To disable Workload Protection, follow the steps for your Agent platform.

### Helm

In the Helm `values.yaml`, set `securityAgent.runtime` to `enabled: false` as follows:

{{< code-block lang="yaml" filename="values.yaml" disable_copy="false" collapsible="true" >}}

# values.yaml file
datadog:

# Set to false to Disable CWS
securityAgent:
  runtime:
    enabled: false
{{< /code-block >}}

### Daemonset/Docker

Apply the following environment variable change to both the System Probe and the Security Agent deployment for a Daemonset:

{{< code-block lang="json" filename="daemon.json" disable_copy="false" collapsible="true" >}}

DD_RUNTIME_SECURITY_CONFIG_ENABLED=false
{{< /code-block >}}

### Host

Modify the `system-probe.yaml` and `security-agent.yaml` to disable the runtime config:

1. Disable CSM in `/etc/datadog-agent/system-probe.yaml`. Ensure that `runtime_security_config` is set to `enabled: false`:
    {{< code-block lang="yaml" filename="system-probe.yaml" disable_copy="false" collapsible="true" >}}

    ##########################################
    ## Security Agent Runtime Configuration ##
    ##                                      ##
    ## Settings to send logs to Datadog are ##
    ## fetched from section `logs_config`   ##
    ## in datadog-agent.yaml                ##
    ##########################################

    runtime_security_config:
    ## @param enabled - boolean - optional - default: false
    ## Set to true to enable full CSM.
    #
    enabled: false

    ## @param fim_enabled - boolean - optional - default: false
    ## Set to true to only enable the File Integrity Monitoring feature.
    # fim_enabled: false

    ## @param socket - string - optional - default: /opt/datadog-agent/run/runtime-security.sock
    ## The full path of the unix socket where the security runtime module is accessed.
    #
    # socket: /opt/datadog-agent/run/runtime-security.sock
    {{< /code-block >}}
2. Disable CSM in `/etc/datadog-agent/security-agent.yaml`. Ensure that `runtime_security_config` is set to `enabled: false`:
    {{< code-block lang="yaml" filename="security-agent.yaml" disable_copy="false" collapsible="true" >}}

    ##########################################
    ## Security Agent Runtime Configuration ##
    ##                                      ##
    ## Settings to send logs to Datadog are ##
    ## fetched from section `logs_config`   ##
    ## in datadog-agent.yaml                ##
    ##########################################

    runtime_security_config:
    ## @param enabled - boolean - optional - default: false
    ## Set to true to enable the Security Runtime Module.
    #
    enabled: false

    ## @param socket - string - optional - default: /opt/datadog-agent/run/runtime-security.sock
    ## The full path of the unix socket where the security runtime module is accessed.
    #
    # socket: /opt/datadog-agent/run/runtime-security.sock
    {{< /code-block >}}
3. Restart your agents.

## Further Reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: /agent/troubleshooting/send_a_flare/?tab=agentv6v7
