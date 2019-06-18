---
title: サポートされているデプロイ シナリオ - WCF
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 2da55176cbfe618b332f2df210e3e1c0516b17ae
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170049"
---
# <a name="supported-deployment-scenarios"></a>サポートされる展開シナリオ

部分的に信頼されたアプリケーションで使用するためにサポートされる Windows Communication Foundation (WCF) 機能のサブセットは、WCF を使用するが、一部のシナリオの要件を満たすために設計されています。 サーバーでは、WCF は、インターネット規模のセキュリティ上の理由から、ASP.NET 2.0 の中程度の信頼アクセス許可でサード パーティ製のアプリケーションを実行する共有ホスティング プロバイダーの設定の要件を満たしています。 クライアントでは、WCF の部分信頼サポートはなどの展開テクノロジの要件を満たすために設計[ClickOnce 配置](/visualstudio/deployment/clickonce-security-and-deployment)または WPF の XAML ブラウザー アプリケーション テクノロジは、シームレスかつセキュリティで保護された展開を許可します。信頼されていないサイトからのデスクトップ アプリケーションです。

## <a name="minimum-permission-requirements"></a>最小権限の要件

WCF には、次の標準の名前付き権限セットのいずれかで実行されるアプリケーションの機能のサブセットがサポートされています。

- 中程度の信頼アクセス許可

- インターネット ゾーン アクセス許可

制限の厳しいアクセス許可が部分的に信頼されたアプリケーションで WCF を使用しようと、実行時にセキュリティ例外が発生する可能性があります。

このようなアクセス許可セットでサポートされる機能の詳細については、「 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)」を参照してください。

## <a name="partial-trust-on-the-server"></a>サーバーでの部分信頼

サービスをホストする ASP.NET Web アプリケーションの多くの商用プロバイダーは、それぞれのサーバーで実行されているアプリケーションが ASP.NET 2.0 の中程度の信頼のアクセス許可セットで実行される要求します。 使用する WCF サービスがこれらの環境で実行できる、 <xref:System.ServiceModel.BasicHttpBinding>、 <xref:System.ServiceModel.WebHttpBinding>、または<xref:System.ServiceModel.WSHttpBinding>トランスポート レベルのセキュリティ。

中程度の信頼ホスティング環境で実行されている WCF サービスは、クライアントの要求に応答の他のサーバーにメッセージを送信して中間層サービスとしても動作できます。 ホスティング環境が適切な <xref:System.Net.WebPermission> をアプリケーションに与えて、目的のサーバーに送信要求を行うようにする場合は、サーバーでの中間層のシナリオがサポートされます。

WCF がサポートしている SOAP メッセージングを使用して、サポートされている SOAP バインディングの 1 つだけでなく、<xref:System.ServiceModel.WebHttpBinding>部分的に信頼されたアプリケーションで Web スタイル サービスを構築するためです。 [WCF Web HTTP プログラミング モデル](wcf-web-http-programming-model.md)、 [WCF 配信](wcf-syndication.md)、および[AJAX の統合と JSON のサポート](ajax-integration-and-json-support.md)WCF の機能がすべて部分信頼でサポートされています。

ワークフロー サービスは完全信頼のアクセス許可を必要とし、部分的に信頼されたアプリケーションでは使用できません。

詳細については、「[方法 :ASP.NET 2.0 で中程度の信頼を使用して、](https://go.microsoft.com/fwlink/?LinkId=84603)します。

## <a name="partial-trust-on-the-client"></a>クライアントでの部分信頼

信頼されていないインターネット サイトからコードをダウンロードして実行する場合、ある程度のセキュリティ対策が必要です。 両方[ClickOnce 配置](/visualstudio/deployment/clickonce-security-and-deployment)部分信頼の WPF の XAML ブラウザー アプリケーション (XBAP) テクノロジの作成を使用して、信頼できないコードに制限されたアクセス許可 (インターネット ゾーン) を付与するとします。

WCF は、いずれかで展開された部分的に信頼されたアプリケーション内からリモート サーバーとの通信に使用できます[ClickOnce 配置](/visualstudio/deployment/clickonce-security-and-deployment)または XBAP します。 インターネット ゾーン アクセス許可のセットが含まれる<xref:System.Net.WebPermission>で説明されている、サポートされている WCF バインドのいずれかを使用して、配信元サーバーとの通信にこれらのアプリケーションの元のホスト用できる[Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>関連項目

- [コード アクセス セキュリティ](../../misc/code-access-security.md)
- [WPF XAML ブラウザー アプリケーションの概要](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [部分信頼](partial-trust.md)
- [ASP.NET の信頼レベルとポリシー ファイル](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
