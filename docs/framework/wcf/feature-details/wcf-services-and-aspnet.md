---
title: WCF サービスと ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: ef772a360ea53c2b5f177ed88ad14c4a1e1277ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637554"
---
# <a name="wcf-services-and-aspnet"></a>WCF サービスと ASP.NET

このトピックでは、ホスト Windows Communication Foundation (WCF) サービスのサイド ASP.NET と ASP.NET 互換モードでホストすることについて説明します。

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>WCF - サイドと ASP.NET をホストしています。

インターネット インフォメーション サービス (IIS) でホストされる WCF サービスは、同じコンピューターでことができます。ASPX ページと 1 つの一般的なアプリケーション ドメイン内の ASMX Web サービス。 ASP.NET では、AppDomain の管理と WCF と ASP.NET HTTP ランタイムの両方の動的なコンパイルなどの一般的なインフラストラクチャ サービスを提供します。 WCF の既定の構成は、サイド バイ サイドで ASP.NET を使用しました。

![WCF サービスおよび ASP .NET を示すスクリーン ショット: 状態を共有します。](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP ランタイムは、ASP.NET 要求の処理が場合でも、同じ AppDomain でこれらのサービスがホストされているは、ASP.NET がコンテンツに WCF サービス宛ての要求の処理に関与しません。 代わりに、WCF サービス モデルは WCF サービス宛てのメッセージをインターセプトし、それを WCF トランスポート/チャネル スタックを介してルーティングします。

この結果、サイド バイ サイド モデルは次のようになります。

- ASP.NET および WCF サービスは、AppDomain の状態を共有できます。 2 つのフレームワークは、同じ AppDomain で共存できる、ため、WCF が ASP.NET (静的変数、イベントなどを含む) を使用した AppDomain の状態を共有できますも。

- WCF サービスのホスティング環境やトランスポートに依存しない、一貫した動作します。 ASP.NET HTTP ランタイムは意図的に、IIS/ASP.NET ホスティング環境や HTTP 通信と強く結合する形で設計されています。 WCF がホスティング環境間で一貫して動作するように設計逆に、(WCF 動作の内部と外部 IIS) やトランスポート (IIS 7.0 でホストされているし、後で、サービスが公開するすべてのエンドポイント間で一貫した動作を持つ場合でもこれらのエンドポイントの一部を使用して、HTTP 以外のプロトコル)。

- 同じ AppDomain 内では、HTTP ランタイムによって実装される機能は、WCF ではなく、ASP.NET コンテンツに適用されます。 ASP.NET アプリケーション プラットフォームの多くの HTTP 固有の機能は、ASP.NET コンテンツが含まれている AppDomain 内でホストされる WCF サービスには適用されません。 このような機能の例を次に示します。

    - HttpContext:<xref:System.Web.HttpContext.Current%2A>は常に`null`WCF サービス内からアクセスする場合。 代わりに、<xref:System.ServiceModel.Channels.RequestContext> を使用してください。

    - ファイル ベースの承認:WCF のセキュリティ モデルは、サービス要求が承認されているかどうかを決定する際に、サービスの .svc ファイルに適用されるアクセス制御リスト (ACL) にはできません。

    - 構成ベースの URL 承認:同様に、WCF のセキュリティ モデルが System.Web ので指定された、URL ベースの承認規則に従っていない\<authorization > 構成要素。 サービスは、ASP で保護された URL 空間に存在する場合、WCF 要求のこれらの設定は無視されます。NET の URL 承認規則。

    - HttpModule の拡張機能:WCF のホスティング インフラストラクチャは、WCF をインターセプト要求、<xref:System.Web.HttpApplication.PostAuthenticateRequest>イベントが発生し、処理は ASP.NET HTTP パイプラインに返されません。 パイプラインの後の段階で要求をインターセプトに設計されたモジュールは、WCF 要求を途中受信できません。

    - ASP.NET impersonation:既定では、WCF に対する要求は常に実行、IIS のプロセス id、System.Web を使用した偽装を有効にする ASP.NET が設定されている場合でも\<identity impersonate ="true"/> 構成オプション。

これらの制限は、IIS アプリケーションでホストされる WCF サービスにのみ適用されます。 WCF の存在によっては、ASP.NET コンテンツの動作は影響はありません。

従来 HTTP パイプラインによって提供される機能を必要とする WCF アプリケーションは、ホストは、トランスポートに依存しませんが、WCF 対応の使用を検討する必要があります。

- <xref:System.ServiceModel.OperationContext> (<xref:System.Web.HttpContext> の代わり)

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> (ASP.NET のファイル ベースまたは URL ベースの承認の代わり)

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> または独自の階層チャネル (HTTP モジュールの代わり)

- System.web による偽装の代わりに WCF を使用して各操作の権限を借用します。

代わりに、WCF の ASP.NET 互換モードで、サービスを実行しているかを検討できます。

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>ASP.NET 互換モードでの WCF サービスをホスト

WCF モデルはホスティング環境やトランスポート一貫した動作に設計されていますが、アプリケーションがこのレベルの柔軟性を必要としない場合も少なくありません。 WCF の ASP.NET 互換モードでは、するか、HTTP 以外のプロトコル経由で通信するために IIS の外部でホストする機能は必要ありませんが、すべての ASP.NET Web アプリケーション プラットフォームの機能を使用するシナリオに適しています。

WCF ホスティング インフラストラクチャは、WCF メッセージを途中受信し、HTTP パイプラインにルーティングする、既定のサイド バイ サイド構成とは異なり ASP.NET 互換モードで実行されている WCF サービスは、ASP.NET の HTTP 要求のライフ サイクルに完全に参加します。 互換モードでの WCF サービスはにより HTTP パイプラインを使用して、<xref:System.Web.IHttpHandler>実装、ASPX ページや ASMX Web サービスの処理方法の要求に似ています。 結果として、WCF の動作と同じ ASMX に関して、次の ASP.NET 機能。

- <xref:System.Web.HttpContext>:ASP.NET 互換モードで実行されている WCF サービスがアクセスできる<xref:System.Web.HttpContext.Current%2A>および関連付けられた状態。

- ファイル ベースの承認:ASP.NET 互換モードで実行されている WCF サービスは、サービスの .svc ファイルをファイル システム アクセス制御リスト (Acl) をアタッチすることによりセキュリティで保護できます。

- URL 承認の設定:ASP します。NET の URL 承認規則は、WCF サービスが ASP.NET 互換モードで実行されている場合、WCF 要求に対して適用されます。

- <xref:System.Web.HttpModuleCollection> 拡張機能:ASP.NET 互換モードで実行されている WCF サービスが ASP.NET の HTTP 要求のライフ サイクルの完全に参加するため HTTP パイプラインで構成されている任意の HTTP モジュールがサービス呼び出しの前後に、WCF 要求で動作するようにします。

- ASP.NET Impersonation:ASP.NET の現在の id を使用して実行する WCF サービスの権限借用スレッドで、アプリケーションの ASP.NET の偽装が有効になっている場合に IIS のプロセス id が異なる可能性があります。 ASP.NET の偽装と WCF の偽装の両方が特定のサービス操作の有効になっているが場合、サービスの実装は WCF から取得した id を使用して最終的に実行されます。

WCF の ASP.NET 互換モードは、次の構成 (アプリケーションの Web.config ファイルにあります) をアプリケーション レベルで有効です。

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

既定値は"`true`"が指定されていない場合。 この値を設定"`false`"アプリケーションで実行されているすべての WCF サービスは ASP.NET 互換モードで実行していないことを示します。

ASP.NET アプリケーション内で実行するかどうか、個々 のサービス実装が制御する機能があるため、ASP.NET 互換モードでは、基本的に、WCF の既定値から異なる要求処理のセマンティクスが示すとおり、互換性モードが有効になっています。 各サービスは、ASP.NET 互換モードをサポートするかどうかを、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> で示すことができます。 この属性の既定値は <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> です。

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

アプリケーション全体を互換モードにしたとき、個々のサービスのサポート レベルがどうなるかを表に示します。

|アプリケーション全体の互換モード設定|AspNetCompatibilityRequirementsMode <br /><br /> 設定|実際の動作|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled ="`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|サービスは正常に動作します。|
|aspNetCompatibilityEnabled ="`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|サービスは正常に動作します。|
|aspNetCompatibilityEnabled ="`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|サービスがメッセージを受信した時点でアクティベーション エラーが発生します。|
|aspNetCompatibilityEnabled ="`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|サービスがメッセージを受信した時点でアクティベーション エラーが発生します。|
|aspNetCompatibilityEnabled ="`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|サービスは正常に動作します。|
|aspNetCompatibilityEnabled ="`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|サービスは正常に動作します。|

> [!NOTE]
> IIS 7.0 と WAS により、HTTP 以外のプロトコル経由で通信する WCF サービス。 ただし、ASP.NET 互換モードを有効にするアプリケーションで実行されている WCF サービスは、非 HTTP エンドポイントを公開するは許可されません。 最初のメッセージを受信した時点で、アクティベーション例外が発生します。

WCF サービスの ASP.NET 互換モードを有効にする方法の詳細については、次を参照してください。<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>と[ASP.NET 互換性](../samples/aspnet-compatibility.md)サンプル。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [AppFabric のホスティング機能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
