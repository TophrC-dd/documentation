---
title: Setting up CSM Pro
kind: documentation
further_reading:
  - link: "/security/cloud_security_management/setup"
    tag: "Documentation"
    text: "Setting up Cloud Security Management"
  - link: "/security/cloud_security_management/misconfigurations/"
    tag: "Documentation"
    text: "Cloud Security Management Misconfigurations"
  - link: "/security/cloud_security_management/vulnerabilities/"
    tag: "Documentation"
    text: "Cloud Security Management Vulnerabilities"
---

The Cloud Security Management (CSM) Pro package includes [CSM Misconfigurations][1] (cloud accounts), [CSM Vulnerabilities][2] (container images), and [Agentless Scanning][6] (container images). To learn more about the available CSM packages, see [Setting up Cloud Security Management][3].

## Getting started

To enable CSM Pro on your infrastructure, complete the following steps:

### Enable resource scanning for cloud accounts

To enable resource scanning for your cloud accounts, you must first set up the integration and then enable CSM for each AWS account, Azure subscription, and Google Cloud project. For detailed instructions, see [Enable CSM Pro for Cloud Accounts][4].

### Enable CSM Pro on the Agent

Set up CSM Pro on the Agent to enable [Kubernetes Security Posture Management][7] for [CSM Misconfigurations][1], and container image metadata collection and [Software Bill of Materials (SBOM)][5] collection for [CSM Vulnerabilities][2].

Select your infrastructure type for details on how to enable CSM Pro on the Agent.

{{< partial name="csm/csm-pro-agent-tiles.html" >}}

## Further reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: /security/cloud_security_management/misconfigurations/
[2]: /security/cloud_security_management/vulnerabilities
[3]: /security/cloud_security_management/setup
[4]: /security/cloud_security_management/setup/csm_pro/cloud_accounts
[5]: https://www.cisa.gov/sbom
[6]: /security/cloud_security_management/agentless_scanning
[7]: /security/cloud_security_management/misconfigurations/frameworks_and_benchmarks/kspm
