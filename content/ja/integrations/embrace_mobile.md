---
app_id: embrace-mobile
app_uuid: 86988058-9b89-45a8-b92f-5473a96e4a36
assets:
  dashboards:
    Embrace Overview: assets/dashboards/embrace_mobile_overview.json
  integration:
    auto_install: true
    configuration: {}
    events:
      creates_events: false
    metrics:
      check:
      - embrace.session_total.five_minute
      - embrace.session_total.hourly
      - embrace.session_total.daily
      - embrace.crash_total.five_minute
      - embrace.crash_total.hourly
      - embrace.crash_total.daily
      - embrace.users_total.daily
      metadata_path: metadata.csv
      prefix: embrace.
    service_checks:
      metadata_path: assets/service_checks.json
    source_type_id: 25653134
    source_type_name: Embrace
author:
  homepage: https://embrace.io
  name: Embrace
  support_email: support@embrace.io
categories:
- 問題追跡
- メトリクス
- モバイル
- ネットワーク
custom_kind: インテグレーション
dependencies:
- https://github.com/DataDog/integrations-extras/blob/master/embrace_mobile/README.md
display_on_public_website: true
draft: false
git_integration_title: embrace_mobile
integration_id: embrace-mobile
integration_title: Embrace Mobile
integration_version: ''
is_public: true
manifest_version: 2.0.0
name: embrace_mobile
public_title: Embrace Mobile
short_description: iOS、Android、React Native、Unity のためのモバイル可観測性
supported_os:
- linux
- windows
- macos
tile:
  changelog: CHANGELOG.md
  classifier_tags:
  - Category::Issue Tracking
  - Category::Metrics
  - Category::Mobile
  - Category::Network
  - Offering::Integration
  - Submitted Data Type::Metrics
  - Supported OS::Linux
  - Supported OS::Windows
  - Supported OS::macOS
  configuration: README.md#Setup
  description: iOS、Android、React Native、Unity のためのモバイル可観測性
  media:
  - caption: Embrace のユーザーセッションリプレイにより、ユーザーセッションの技術的および行動的詳細を時間単位で視覚化。問題を手動で再生しなくても、根本原因をすばやく認識できます。
    image_url: images/embrace_session.jpg
    media_type: image
  - caption: タイミング、結果、そしてユーザーアクションを追跡して主要なユーザーフローを最適化。動作の遅延やフリーズに不満を感じたユーザーが使用を放棄した箇所をすばやく特定、修正し、エンゲージメントおよび収益の強化を図ります。
    image_url: images/embrace_app_performance.jpg
    media_type: image
  - caption: リアルタイムダッシュボードで主要なメトリクスを監視。パフォーマンス、安定性、エンゲージメント、収益化などを簡単に追跡できるため、チームは重要なデータに注力できます。
    image_url: images/embrace_dashboard.jpg
    media_type: image
  overview: README.md#Overview
  support: README.md#Support
  title: Embrace Mobile
---

<!--  SOURCED FROM https://github.com/DataDog/integrations-extras -->


## 概要

[Embrace][1] は、モバイルチームが最高のユーザー体験を提供できるよう、パフォーマンスの最適化、問題の優先順位付けと修正作業、そして機能やリリース、カスタムセグメントの監視を可能にするモバイル可観測性およびデータのプラットフォームです。Embrace では、複雑なモバイルデータをアクションに変換できます。あらゆるすべてのユーザーエクスペリエンスの包括的なセッションレベルデータを収集することで、Embrace は強力なインサイトを抽出しビジネスの成長を促進します。

アプリをインストールすると、Embrace のダッシュボードでモバイルの主要なヘルスメトリクスを追跡できるようになります。パフォーマンスの低下があった場合、手動でユーザーセッションを再生しなくても、影響のあったセッションの完全な詳細を調査することができます。

## セットアップ

1. 無料トライアルを開始し、[Embrace のドキュメント][2]に従ってください。**Datadog でメトリクスを見る前に、このドキュメントに従う必要があります**。
1. Embrace インテグレーションのセットアップが完了したら、Datadog に戻り両プラットフォームを接続します。
1. 認証情報を使用してログインし、Embrace アカウントを認証して Datadog に接続します。

## サポート

ご不明な点は、[Datadog のサポートチーム][3]までお問合せください。

[1]: https://embrace.io
[2]: https://embrace.io/docs/
[3]: https://docs.datadoghq.com/ja/help/