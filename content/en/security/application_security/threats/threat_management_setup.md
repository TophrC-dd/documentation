---
title: App and API Protection Setup
disable_toc: false
---

## Prerequisites

Before setting up App and API Protection, ensure the following prerequisites are met:

- **Datadog Agent Installation:** The Datadog Agent is installed and configured for your application's operating system or container, cloud, or virtual environment.
- Datadog APM Configuration: Datadog APM is configured for your application or service, and web traces (`type:web`) are being received by Datadog.
- Supported Tracing Library: The Datadog Tracing Library used by your application or service supports App and API Protection capabilities for the language of your application or service. For more details, refer to the Library Compatibility page.

## App and API Protection enablement types overview

There are two main approaches to enable App and API Protection on your tracing libraries: Single-Step Instrumentation and Datadog Tracing Libraries.

## Single-Step Instrumentation

Run a one-line install command to install the Datadog Agent, and enable App and API Protection with Single-Step Instrumentation.


## Datadog Tracing Libraries

Add an environment variable or a new argument to your Datadog Tracing Library configuration.

## Further Reading

{{< partial name="whats-next/whats-next.html" >}}