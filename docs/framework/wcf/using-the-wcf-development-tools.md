---
title: WCF 開発ツールの使用
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 1ffa3be4a6b8976ab978ea995e8b2c1faaacf0ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144639"
---
# <a name="using-the-wcf-development-tools"></a>WCF 開発ツールの使用
このセクションでは、WCFservice の開発に役立つ Visual Studio 開発ツールについて説明します。  
  
 基盤として、Visual Studio テンプレートを使用して、独自のサービスを迅速に構築し、WCF サービスの自動ホストと WCF テスト クライアントを使用して、サービスをデバッグおよびテストすることができます。 これらのツールによって、高速でシームレスなデバッグとテストのサイクルが実現し、初期の段階においてホスト モデルのコミットが必要なくなります。  
  
## <a name="the-wcf-developer-tools"></a>WCF の開発者用ツール  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Visual Studio で、定義済みの Visual Studio プロジェクトと項目テンプレートを使用すると、WCF サービスや周辺アプリケーションを迅速に構築します。  
  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 WCF サービスの自動ホスト (WcfSvcHost.exe) を使用すると、自動的にホストし、実装したサービスをテストするには、(F5) Visual Studio デバッガーを起動できます。 WCF テスト クライアント (wcfTestClient.exe) または独自のクライアントを検出して潜在的なエラーを修正するを使用してサービスをテストできます。  
  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 WCF テスト クライアント (WcfTestClient.exe) は、任意の型のパラメーターを入力し、サービス、およびサービスの応答を送り返しますビューへの入力を送信するための GUI ツールです。 テストを行う WCF サービスの自動ホストと組み合わせたときに、シームレスにサービスを提供します。  
  
 [XML からのデータ型クラスの生成](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 クリップボードに格納されている XML データは、コード ページに貼り付けることができます。 データで定義されているクラスは、コード型に変換されます。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>管理特権を必要としないツールの使用  
 WCF サービスの開発を管理者特権のないユーザーを有効にする ACL (アクセス制御リスト) は、名前空間の作成"http://+:8731/Design_Time_Addresses"Visual Studio のインストール中にします。 この ACL は (UI) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。 管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、既定の構成で、WCF テンプレートまたは WF テンプレートでデータを送受信できるようになります。 また、ユーザーが管理者特権を与えずに WCF サービスの自動ホスト (wcfSvcHost.exe) を使用することもできます。  
  
 システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の Netsh.exe ツールを使用すると、アクセスを変更できます。 Netsh.exe の使用例を次に示します。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe の詳細については、次を参照してください。 [Netsh.exe ツールとコマンド ライン スイッチを使用する方法](https://go.microsoft.com/fwlink/?LinkId=97877)します。  
  
## <a name="see-also"></a>関連項目

- [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)
- [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
