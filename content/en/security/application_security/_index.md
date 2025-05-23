---
title: App and API Protection
description: Monitor threats targeting production system, leveraging the execution context provided by distributed traces.
aliases:
  - /security_platform/application_security
  - /security/application_security/enabling/single_step
  - /security/application_security/enabling/compatibility
  - /security/application_security/enabling
  - /security/application_security/getting_started
further_reading:
- link: "/security/application_security/how-it-works/"
  tag: "Documentation"
  text: "How App and API Protection Works"
- link: "/security/application_security/threats/"
  tag: "Documentation"
  text: "App and API Protection"
- link: "/security/code_security/software_composition_analysis/"
  tag: "Documentation"
  text: "Software Composition Analysis"
- link: "https://www.datadoghq.com/product/security-platform/application-security-monitoring/"
  tag: "Product Page"
  text: "Datadog App and API Protection"
- link: "https://www.datadoghq.com/blog/apm-security-view/"
  tag: "Blog"
  text: "Gain visibility into risks, vulnerabilities, and attacks with APM Security View"
- link: "https://www.datadoghq.com/blog/aws-waf-datadog/"
  tag: "Blog"
  text: "Monitor AWS WAF activity with Datadog"
- link: "https://www.datadoghq.com/blog/security-inbox-prioritization/"
  tag: "Blog"
  text: "How Datadog Security Inbox prioritizes security risks"
- link: "https://www.datadoghq.com/blog/understanding-your-waf/"
  tag: "Blog"
  text: "Understanding your WAF: How to address common gaps in web application security"
- link: "https://www.datadoghq.com/blog/mitigate-account-takeovers/"
  tag: "Blog"
  text: "Mitigate account takeovers with Datadog App and API Protection"
algolia:
  tags: ["asm", "App and API Protection"]
---

{{< site-region region="gov" >}}
<div class="alert alert-warning">App and API Protection is not supported for your selected <a href="/getting_started/site">Datadog site</a> ({{< region-param key="dd_site_name" >}}).</div>
{{< /site-region >}}

{{< img src="/security/application_security/app-sec-landing-page.png" alt="A security signal panel in Datadog, which displays attack flows and flame graphs" width="75%">}}

Datadog App and API Protection (AAP) provides protection against application-level attacks that aim to exploit code-level vulnerabilities, such as Server-Side-Request-Forgery (SSRF), SQL injection, Log4Shell, and Reflected Cross-Site-Scripting (XSS). You can monitor and protect apps hosted directly on a server, Docker, Kubernetes, Amazon ECS, and (for supported languages) AWS Fargate.

AAP leverages Datadog [tracing libraries][1], and the [Datadog Agent][2] to identify services exposed to application attacks. Once configured, AAP leverages in-app detection rules to detect and protect against threats in your application environment and trigger security signals whenever an attack impacts your production system, or a vulnerability is triggered from the code.

When a threat is detected, a security signal is generated in Datadog. For `HIGH` or `CRITICAL` severity security signals, notifications can be sent to Slack, email, or PagerDuty to notify your team and provide real-time context around threats.

Once a security signal is triggered, quickly pivot to investigate and protect in Datadog. Leverage the deep observability data provided by AAP and APM distributed tracing, in one view, to resolve application issues. Analyze attack flows, view flame graphs, and review correlated trace and log data to pinpoint application vulnerabilities. Eliminate context switching by flowing through application data into remediation and mitigation steps, all within the same panel.

With AAP, you can cut through the noise of continuous trace data to focus on securing and protecting your environment.

Until you fully remediate the potential vulnerabilities in your application code, AAP enables you to slow down attackers by blocking their IPs temporarily or permanently, with a single click.

## Understanding how App and API Protection is implemented in Datadog

If you're curious how App and API Protection is structured and how it uses tracing data to identify security problems, read [How App and API Protection Works][3].

## Configure your environment

Powered by provided [out-of-the-box rules][4], AAP detects threats without manual configuration. If you already have Datadog [APM][1] configured on a physical or virtual host, setup only requires setting one environment variable to get started.

To start configuring your environment to detect and protect threats with AAP, follow the enabling documentation for each product. Once AAP is configured, you can begin investigating and remediating security signals in the [Security Signals Explorer][6].

## Investigate and remediate security signals

In the [Security Signals Explorer][6], click on any security signal to see what happened and the suggested steps to mitigate the attack. In the same panel, view traces with their correlated attack flow and request information to gain further context.

## Disable AAP
For information on disabling AAP or its features, see the following:

- [Disabling threat management and protection][10]

## Next steps

{{< partial name="whats-next/whats-next.html" >}}

[1]: /tracing/
[2]: /agent/
[3]: /security/application_security/how-it-works/
[4]: /security/default_rules/?category=cat-application-security
[6]: https://app.datadoghq.com/security
[7]: https://dashcon.io/appsec
[8]: /security/code_security/software_composition_analysis/
[9]: /security/code_security/
[10]: /security/application_security/troubleshooting/#disabling-threat-management-and-protection
[11]: /security/application_security/troubleshooting/#disabling-software-composition-analysis
[12]: /security/application_security/troubleshooting/#disabling-code-security
