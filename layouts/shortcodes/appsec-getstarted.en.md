
## Prerequisites

<div class="alert alert-info"><strong>1-Click Enablement</strong><br>
If your service is running with <a href="/agent/guide/how_rc_works/#enabling-remote-configuration">an Agent with Remote Configuration enabled and a tracing library version that supports it</a>, hover over the <strong>Not Enabled</strong> indicator in the AAP Status column and click <strong>Enable AAP</strong>. There's no need to re-launch the service with the <code>DD_APPSEC_ENABLED=true</code> or <code>--enable-appsec</code> flags.</div>

- The [Datadog Agent][101] is installed and configured for your application's operating system or container, cloud, or virtual environment. 
- [Datadog APM][103] is configured for your application or service, and traces are being received by Datadog. 
- If your service is running with [an Agent with Remote Configuration enabled and a tracing library version that supports it][104], you can block attackers from the Datadog UI without additional configuration of the Agent or tracing libraries.

[101]: https://app.datadoghq.com/account/settings#agent
[102]: https://app.datadoghq.com/services?lens=Security
[103]: /tracing/trace_collection/dd_libraries/
[104]: /agent/remote_config/?tab=configurationyamlfile#enabling-remote-configuration