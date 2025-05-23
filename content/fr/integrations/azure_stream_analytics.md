---
aliases:
- /fr/integrations/azure_streamanalytics
categories:
- cloud
- azure
custom_kind: integration
dependencies: []
description: Surveillez des métriques clés d'Azure Stream Analytics.
doc_link: https://docs.datadoghq.com/integrations/azure_stream_analytics/
draft: false
git_integration_title: azure_stream_analytics
has_logo: true
integration_id: azure-streamanalytics
integration_title: Microsoft Azure Stream Analytics
integration_version: ''
is_public: true
manifest_version: '1.0'
name: azure_stream_analytics
public_title: Intégration Datadog/Microsoft Azure Stream Analytics
short_description: Surveillez des métriques clés d'Azure Stream Analytics.
version: '1.0'
---

<!--  SOURCED FROM https://github.com/DataDog/dogweb -->
## Section Overview

Azure Stream Analytics est un moteur de traitement d'événements conçu pour analyser d'importants volumes de données diffusées à partir d'appareils.

Utilisez l'intégration Datadog/Azure pour recueillir des métriques d'Azure Stream Analytics.

## Configuration

### Installation

Si vous ne l'avez pas déjà fait, configurez d'abord [l'intégration Microsoft Azure][1]. Aucune autre procédure d'installation n'est requise.

## Données collectées

### Métriques
{{< get-metrics-from-git "azure_stream_analytics" >}}


### Événements

L'intégration Azure Stream Analytics n'inclut aucun événement.

### Checks de service

L'intégration Azure Stream Analytics n'inclut aucun check de service.

## Dépannage

Besoin d'aide ? Contactez [l'assistance Datadog][3].

[1]: https://docs.datadoghq.com/fr/integrations/azure/
[2]: https://github.com/DataDog/dogweb/blob/prod/integration/azure_stream_analytics/azure_stream_analytics_metadata.csv
[3]: https://docs.datadoghq.com/fr/help/