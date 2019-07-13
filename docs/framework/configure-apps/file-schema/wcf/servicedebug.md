---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 7b7526dbcbd1948d3d8a27d146efd0462fefaca5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788441"
---
# <a name="servicedebug"></a>\<serviceDebug >
Windows Communication Foundation (WCF) サービスのデバッグおよびヘルプ情報機能を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceDebug >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|httpHelpPageBinding|HTTP を利用してサービス ヘルプ ページにアクセスする場合に使用するバインディングの種類を指定する文字列値。<br /><br /> <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> をサポートする内部バインディング要素を使用したバインディングでのみサポートされます。 さらに、バインディングの <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> プロパティが <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> である必要があります。|  
|httpHelpPageBindingConfiguration|このバインディングの追加の構成情報を参照する `httpHelpPageBinding` 属性に指定されるバインディングの名前を指定する文字列。 同じ名前を `<bindings>` セクションに定義する必要があります。|  
|httpHelpPageEnabled|WCF が HTML ヘルプ ページで指定されたアドレスで公開するかどうかをその制御するブール値、`httpHelpPageUrl`属性。 既定値は `true` です。<br /><br /> このプロパティを `false` に設定して、HTML ブラウザーに表示される HTML ヘルプ ページの公開を無効にできます。<br /><br /> HTML ヘルプ ページが、`httpHelpPageUrl` 属性により制御される場所に公開されるようにするには、この属性を `true` に設定する必要があります。 さらに、次のいずれかの条件も満たす必要があります。<br /><br /> -`httpHelpPageUrl`属性は、HTTP プロトコル スキームをサポートする絶対アドレスです。<br />-HTTP プロトコル スキームをサポートするサービスのベース アドレスがあります。<br /><br /> HTTP プロトコル スキームをサポートしない絶対アドレスが `httpHelpPageUrl` 属性に割り当てられている場合は例外がスローされますが、前の基準をどれも満たさないその他のシナリオでは、例外も HTML ヘルプ ページも表示されません。|  
|httpHelpPageUrl|HTML ブラウザーを使用してエンドポイントを表示するときにユーザーが参照する、カスタム HTML ヘルプ ファイルの相対的または絶対的な HTTP ベースの URL を指定する URI。<br /><br /> この属性を使用して、HTTP/Get 要求から返されるカスタム HTML ヘルプ ファイルを HTML ブラウザーなどから利用できます。 HTML ヘルプ ファイルの位置は、次のように解決されます。<br /><br /> 1.この属性の値が相対アドレスの場合、HTML ヘルプ ファイルの位置は、HTTP 要求をサポートするサービスのベース アドレスにこのプロパティの値を加えた値になります。<br />2.この属性が絶対アドレスであり、HTTP 要求をサポートする場合は、HTML ヘルプ ファイルの位置はこのプロパティの値になります。<br />3.この属性の値が絶対値であっても HTTP 要求をサポートしていない場合は、例外がスローされます。<br /><br /> この属性は、有効な場合にのみ、`httpHelpPageEnabled`属性が`true`します。|  
|httpsHelpPageBinding|HTTPS を利用してサービス ヘルプ ページにアクセスする場合に使用するバインディングの種類を指定する文字列値。<br /><br /> <xref:System.ServiceModel.Channels.IReplyChannel> をサポートする内部バインディング要素を使用したバインディングでのみサポートされます。 さらに、バインディングの <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> プロパティが <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> である必要があります。|  
|httpsHelpPageBindingConfiguration|このバインディングの追加の構成情報を参照する `httpsHelpPageBinding` 属性に指定されるバインディングの名前を指定する文字列。 同じ名前を `<bindings>` セクションに定義する必要があります。|  
|httpsHelpPageEnabled|WCF が HTML ヘルプ ページで指定されたアドレスで公開するかどうかをその制御するブール値、`httpsHelpPageUrl`属性。 既定値は `true` です。<br /><br /> このプロパティを `false` に設定して、HTML ブラウザーに表示される HTML ヘルプ ページの公開を無効にできます。<br /><br /> HTML ヘルプ ページが、`httpsHelpPageUrl` 属性により制御される場所に公開されるようにするには、この属性を `true` に設定する必要があります。 さらに、次のいずれかの条件も満たす必要があります。<br /><br /> -`httpsHelpPageUrl`属性は、HTTPS プロトコル スキームをサポートする絶対アドレスです。<br />-HTTPS プロトコル スキームをサポートするサービスのベース アドレスがあります。<br /><br /> HTTPS プロトコル スキームをサポートしない絶対アドレスが `httpsHelpPageUrl` 属性に割り当てられている場合は例外がスローされますが、前の基準をどれも満たさないその他のシナリオでは、例外も HTML ヘルプ ページも表示されません。|  
|httpsHelpPageUrl|HTML ブラウザーを使用してエンドポイントを表示するときにユーザーが参照する、カスタム HTML ヘルプ ファイルの相対的または絶対的な HTTPS ベースの URL を指定する URI。<br /><br /> この属性を使用して、HTTPS/Get 要求から返されるカスタム HTML ヘルプ ファイルを HTML ブラウザーなどから利用できます。 HTML ヘルプ ファイルの場所は、次のように解決されます。<br /><br /> -このプロパティの値が相対アドレスである場合、HTML ヘルプ ファイルの位置は、HTTPS 要求をサポートするサービスのベース アドレスの値を加えたこのプロパティの値を使用します。<br />-このプロパティの値が絶対アドレスで HTTPS 要求をサポートあり場合、HTML ヘルプ ファイルの場所は、このプロパティの値です。<br />-このプロパティの値が絶対値であって、HTTPS 要求をサポートしていない場合、例外がスローされます。<br /><br /> この属性は、有効な場合にのみ、`httpHelpPageEnabled`属性が`true`します。|  
|includeExceptionDetailInFaults|デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージド例外情報を含めるかどうかを指定する値。 既定値は、`false` です。<br /><br /> この属性を `true` に設定すると、デバッグ目的でクライアントへのマネージド例外情報のフロー、および Web ブラウザーでサービスをブラウズするユーザー向けの HTML 情報ファイルの公開を有効にできます。 **注意:** マネージド例外情報をクライアントに返すことは、セキュリティ リスクになり得ます。 これは、例外の詳細が、認証されていないクライアントによって使用可能な内部サービスの実装に関する情報を公開するためです。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 設定`includeExceptionDetailInFaults`に`true`により例外を使用して宣言されていない場合でも、アプリケーション コードによってスローされる例外を返すサービス、<xref:System.ServiceModel.FaultContractAttribute>します。 この設定は、サーバーが予期しない例外をスローしている場合のデバッグ時に役立ちます。 この属性を使用すると、不明な例外がシリアル化された形式で返されるので、例外をより詳細に調べることができます。  
  
> [!CAUTION]
>  マネージ例外情報をクライアントに戻すことは、セキュリティ リスクになり得ます。これは、例外の詳細が、非承認のクライアントで使用可能な内部サービスの実装についての情報を公開するからです。 セキュリティの問題にかかわるため、この操作は制御されたデバッグ シナリオでのみ行うことを強くお勧めします。 アプリケーションを配置する場合は、`includeExceptionDetailInFaults` を `false` に設定する必要があります。  
  
 マネージ例外に関連するセキュリティの問題に関する詳細については、次を参照してください。[を指定すると処理のエラー コントラクトおよびサービスの](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)します。 コード サンプルは、次を参照してください。[サービス デバッグ動作](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)します。  
  
 `httpsHelpPageEnabled` と `httpsHelpPageUrl` を設定して、ヘルプ ページを有効または無効にすることもできます。 各サービスは、サービスの WSDL を取得するエンドポイントなど、サービスに関する情報が含まれるヘルプ ページをオプションで公開できます。 これを有効にするには、`httpHelpPageEnabled` プロパティを `true` に設定します。 これにより、サービスのベース アドレスへの GET 要求に対して、ヘルプ ページを返すことができます。 このアドレスは、`httpHelpPageUrl` 属性を設定することで変更できます。 また、HTTP の代わりに HTTPS を使用すると、このアドレスをセキュリティで保護できます。  
  
 省略可能な `httpHelpPageBinding` 属性および `httpHelpPageBinding` 属性を使用すると、サービス ウェブ ページにアクセスするためのバインディングを構成できます。 これらの属性が指定されていない場合、サービス ヘルプ ページへのアクセスには、適切な既定のバインディグ (HTTP の場合は `HttpTransportBindingElement`、HTTPS の場合は `HttpsTransportBindingElement`) が使用されます。 これらの属性は、組み込みの WCF バインディングでは使用できないことに注意してください。 バインディング xref:System.ServiceModel.Channels.IReplyChannel をサポートする内部バインディング要素でのみ > がサポートされます。 さらに、バインディングの <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> プロパティが <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> である必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [コントラクトおよびサービスのエラーの指定と処理](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [例外とエラーの処理](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [サービス デバッグ動作](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
