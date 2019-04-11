---
title: COM アプリケーションとの統合の概要
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 182e5f41498d8f5e3fcbc4b84aa7e86b67ce3ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087626"
---
# <a name="integrating-with-com-applications-overview"></a>COM アプリケーションとの統合の概要
Windows Communication Foundation (WCF) は、マネージ コードを開発者には、接続型アプリケーションを作成するための豊富な環境を提供します。 ただし、アンマネージ COM ベースのコードにかなりの投資がある、移行したくない場合は、まだ統合できます WCF Web サービスの既存のコードに直接 WCF サービス モニカーを使用しています。 サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。  
  
> [!NOTE]
>  サービス モニカーでは、WCF の通信チャネルを使用して、すべての通信。 このチャネルのセキュリティ メカニズムと識別メカニズムは、標準の COM および DCOM プロキシで使用されるものとは異なります。 さらに、サービス モニカーは WCF 通信チャネルは、既定のタイムアウト期間を使用するためには、1 分間のすべての呼び出しです。  
  
 サービス モニカーを併用、 `GetObject` WCF Web サービスを呼び出すための厳密に型指定された、COM に固有の方法で、アンマネージ開発者を提供する関数。 これは、ローカル、WCF Web サービスのコントラクトおよび使用するバインディングの定義を COM から参照できる必要があります。 他の WCF クライアントのようにこのチャネルの構築は、最初のメソッド呼び出し時に COM プログラマに対して透過的に実行が、サービス モニカーは、サービスに型指定されたチャネルを作成する必要があります。  
  
 他の WCF クライアント、モニカーを使用する場合、共通のアプリケーションは、アドレス、バインド、およびサービスと通信するコントラクトを指定します。 コントラクトは、次のいずれかの方法で指定できます。  
  
-   型指定のあるコントラクト - クライアント コンピューターで COM から参照できる型として登録されます。  
  
-   WSDL コントラクト - WSDL ドキュメントという形で供給されます。  
  
-   MEX コントラクト - 実行時に Metadata Exchange (MEX) エンドポイントから取得されます。  
  
## <a name="parameters-supported-by-the-service-moniker"></a>サービス モニカーでサポートされるパラメーター  
 サービス モニカーでサポートされるパラメーターを次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`address`|サービスの URL 位置。|  
|`binding`|アプリケーション構成のバインディング セクションの名前。|  
|`bindingConfiguration`|名前付きバインディング セクション内の名前付きバインディング インスタンス。|  
|`contract`|サービス コントラクトまたは (MEX の) コントラクト名を表すインターフェイス識別子 (IID)。|  
|`wsdl`|代替形式のコントラクト定義を提供する WSDL ドキュメント。|  
|`spnIdentity`|サービスとの通信に使用するサーバー プリンシパル名 (SPN) ID。|  
|`upnIdentity`|サービスとの通信に使用するユーザー プリンシパル名 (UPN) ID。|  
|`dnsIdentity`|サービスとの通信に使用する DNS ID。|  
|`mexAddress`|サービスの Metadata Exchange (MEX) エンドポイントの URL 位置。|  
|`mexBinding`|MEX エンドポイントと接続するための、アプリケーション構成のバインディング セクションの名前。|  
|`mexBindingConfiguration`|MEX エンドポイントと接続する名前付きバインディング セクション内の名前付きバインディング インスタンス。|  
|`bindingNamespace`|取得する MEX のバインディング セクション名の名前空間。|  
|`contractNamespace`|取得する MEX のコントラクトの名前空間。|  
|`mexSpnIdentity`|MEX エンドポイントとの通信に使用するサーバー プリンシパル名 (SPN) ID。|  
|`mexUpnIdentity`|MEX エンドポイントとの通信に使用するユーザー プリンシパル名 (UPN) ID。|  
|`mexDnsIdentity`|MEX エンドポイントとの通信に使用する DNS ID。|  
|`serializer`|"XML" シリアライザーと "datacontract" シリアライザーのいずれを使用するかを指定します。|  
  
> [!NOTE]
>  完全な COM ベースのクライアントと共に使用している場合でもサービス モニカーには、クライアント コンピューターにインストールするには、WCF とサポートの .NET Framework 2.0 が必要です。 また、サービス モニカーを使用するクライアント アプリケーションには、適切なバージョンの .NET Framework ランタイムが読み込まれていることが重要です。 Office アプリケーション内でモニカーを使用する場合、構成ファイルに、正しいフレームワーク バージョンが読み込まれていることを確認する必要があります。 たとえば Excel の場合、Excel.exe ファイルと同じディレクトリにある Excel.exe.config というファイルに、次のテキストが記述されている必要があります。  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>関連項目

- [方法: サービス モニカーを登録および構成する](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
