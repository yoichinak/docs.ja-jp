---
title: アプリケーション シナリオ (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, learn more
- WCF Data Services, scenarios
ms.assetid: 7c82658f-e7c0-46b6-834d-6592f67ab5ea
ms.openlocfilehash: 9e70e2fff0bee22bcb7d7668f33302f7e7013117
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273136"
---
# <a name="application-scenarios-wcf-data-services"></a>アプリケーション シナリオ (WCF Data Services)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]は、データをフィードとして公開および使用する[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]ための主要なシナリオのセットをサポートしています。 このトピックでは、これらのシナリオに関連するトピックを紹介します。

データベースからリレーショナルデータを[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードとして公開します。

- [クイック スタート](quickstart-wcf-data-services.md)

- [サービスとしてのデータの公開](exposing-your-data-as-a-service-wcf-data-services.md)

- [方法: ADO.NET Entity Framework データソースを使用してデータサービスを作成する](create-a-data-service-using-an-adonet-ef-data-wcf.md)

任意の CLR データ クラスを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開する。

- [サービスとしてのデータの公開](exposing-your-data-as-a-service-wcf-data-services.md)

- [方法: リフレクションプロバイダーを使用してデータサービスを作成する](create-a-data-service-using-rp-wcf-data-services.md)

- [Data Services プロバイダー](data-services-providers-wcf-data-services.md)

.NET Framework ベースのクライアント アプリケーションの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する。

- [クイック スタート](quickstart-wcf-data-services.md)

- [クライアント アプリケーションでのデータ サービスの使用](using-a-data-service-in-a-client-application-wcf-data-services.md)

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)

Silverlight ベースのクライアント アプリケーションの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する。

- [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))

- [非同期操作](asynchronous-operations-wcf-data-services.md)

- [方法: データサービスデータをコントロールにバインドする (Silverlight クライアント)](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee681614(v=vs.103))

AJAX ベースのクライアント アプリケーションの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する。

- [クライアント アプリケーションでのデータ サービスの使用](using-a-data-service-in-a-client-application-wcf-data-services.md)

- [ODataURI 規則](https://go.microsoft.com/fwlink/?LinkId=185564)

- [ODataJavaScript Object Notation (JSON) 形式](https://go.microsoft.com/fwlink/?LinkId=185790)

を使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]してクライアントとサーバーの間でデータを転送するエンドツーエンドのデータソリューションを作成します。

- [クイック スタート](quickstart-wcf-data-services.md)

- [クライアント アプリケーションでのデータ サービスの使用](using-a-data-service-in-a-client-application-wcf-data-services.md)

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)

クライアントの待機時間に伴う問題を回避するために [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを非同期で使用する .NET Framework ベースのクライアント アプリケーションを作成する。

- [方法: 非同期データサービスクエリの実行](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)

- [非同期操作](asynchronous-operations-wcf-data-services.md)

- [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))

ストリームとして[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]アクセスおよび変更されるバイナリラージオブジェクトを使用して、フィードを公開および使用します。

- [ストリーミング プロバイダー](streaming-provider-wcf-data-services.md)

- [バイナリ データの操作](working-with-binary-data-wcf-data-services.md)

フィード[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]を Windows Presentation Framework (WPF) アプリケーションのコントロールにバインドします。

- [コントロールへのデータのバインド](binding-data-to-controls-wcf-data-services.md)

- [方法: Windows Presentation Foundation 要素にデータをバインドする](bind-data-to-wpf-elements-wcf-data-services.md)

- [方法: プロジェクトデータソースを使用してデータをバインドする](how-to-bind-data-using-a-project-data-source-wcf-data-services.md)

データ サービスへのメッセージを先に取得してクエリのデータ検証およびロール ベースのフィルター処理を実行する。

- [方法: データサービスメッセージのインターセプト](how-to-intercept-data-service-messages-wcf-data-services.md)

- [インターセプター](interceptors-wcf-data-services.md)

データ サービス上にエンドポイントを作成してカスタム サービスの動作を有効にする。

- [方法: サービス操作の定義](how-to-define-a-service-operation-wcf-data-services.md)

- [サービス操作](service-operations-wcf-data-services.md)

## <a name="see-also"></a>関連項目

- [クイック スタート](quickstart-wcf-data-services.md)
- [リソース](wcf-data-services-resources.md)
