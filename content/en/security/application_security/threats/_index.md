---
title: App and API Protection
further_reading:
- link: "/security/application_security/how-it-works/add-user-info/"
  tag: "Documentation"
  text: "Tracking User Activity"
- link: "/security/application_security/threats/library_configuration/"
  tag: "Documentation"
  text: "Configuring your AAP setup"
- link: "/security/code_security/software_composition_analysis/"
  tag: "Documentation"
  text: "Software Composition Analysis"
- link: "/security/application_security/how-it-works/"
  tag: "Documentation"
  text: "How AAP Works"
---

{{< site-region region="gov" >}}
<div class="alert alert-warning">App and API Protection is not supported for your selected <a href="/getting_started/site">Datadog site</a> ({{< region-param key="dd_site_name" >}}).</div>
{{< /site-region >}}

Datadog's App and API Protection (AAP) App and API Protection protects web applications and APIs from a wide range of security threats, including: 

- Exploit attempts
- Application abuse and fraud
- API abuse 

Integrated into the Datadog platform, App and API Protection leverages Datadog’s extensive observability data (logs and traces) to provide full-stack visibility and security in a unified platform. 

App and API Protection enables teams to identify and remediate threats quickly. Its key differentiator is bridging the gap between security and DevOps, promoting collaboration between development, security, and operations teams.

## Use cases

Discover the ways Datadog App and API Protection helps common use cases:

| You want to...    | How Datadog AAP can help |
| ----------- | ----------- |
| **Web Application Protection:** Prevent vulnerability exploits such as SQL Injection, Server-side Request Forgery, and Local File Inclusion. | Enable [Exploit Prevention][9] on your services. App and API Protection blocks exploits in real-time and generates signals for further investigation.|
| **Application and API abuse:** Protect applications against application and API abuse such as credential stuffing and Account Takeover attacks.| Leverage [OOTB detection rules][10] for notifications such as unusual account creations or password resets from an IP, or distributed credential stuffing campaigns. Review the benefits of [OOTB Account TakeOver Protection][11].|
| **API Security:** Learn about your organization’s APIs, understand the posture and actions needed to reduce risk using a prioritized list of API endpoints.| App and API Protection:</br> - Inventories all your API endpoints.</br> - Gives you visibility into your API traffic, including API abuse.</br> - Highlights risk across your API endpoints. For example, vulnerable or unauthenticated endpoints processing sensitive data.|

## Security signals

Security signals raised by Threat Monitoring are summarized and surfaced in views you already commonly visit to monitor service health and performance. The [Software Catalog][1] and individual Service Pages in APM provide insights into application threat signals, allowing you to investigate vulnerabilities, block attackers, and review attack exposures.

{{< img src="security/application_security/threats/threats-on-svc-cat_3.png" alt="Software Catalog with services showing threat signals" style="width:100%;" >}}

For additional information about how App and API Protection works, read [How AAP Works][4].


## Explore threat signals

When threat data for your services is coming into Datadog, [AAP Overview][7] shows a summary of what's happening. Here, you can enable vulnerability detection, review attacks, customize alerting and reporting, and enable AAP on your services. To investigate signals of suspicious activity, click a service's **Review** link.

In the [Signals Explorer][2], filter by attributes and facets to find critical threats. Click into a signal to see details for it, including the user information and their IP address, what rule they triggered, attack flow, and related traces and other security signals. From this page you can also click to create a case and declare an incident. For more information see [Investigate Security Signals][8].

{{< img src="security/application_security/threats/appsec-threat-overview.png" alt="Overview of investigating threats in signals explorer">}}


## Create In-App WAF rules for identifying attack patterns

You can [create In-App WAF rules][5] that define what suspicious behavior looks like in your application, augmenting the default rules that come with AAP. Then [specify custom rules][6] to generate security signals from the attack attempts triggered from these rules, raising them in the Threat Monitoring views for your investigation.

## Slow down attacks and attackers with AAP Protect

{{% asm-protect %}}

## Disable threat management and protection

For information on disabling threat management and protection, see [Disabling threat management and protection][12].

## Further reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: https://app.datadoghq.com/services?lens=Security
[2]: https://app.datadoghq.com/security?query=%40workflow.rule.type%3A%22Application%20Security%22&column=time&order=desc&product=appsec&viz=stream&start=1694726477747&end=1695331277747&paused=false
[4]: /security/application_security/how-it-works/
[5]: /security/application_security/threats/inapp_waf_rules/
[6]: /security/application_security/policies/custom_rules/
[7]: https://app.datadoghq.com/security/appsec?
[8]: /security/workload_protection/security_signals/
[9]: /security/application_security/exploit-prevention/
[10]: /security/default_rules/?category=cat-application-security
[11]: /security/account_takeover_protection/
[12]: /security/application_security/troubleshooting/#disabling-threat-management-and-protection
