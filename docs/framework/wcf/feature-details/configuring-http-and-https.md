---
title: HTTP および HTTPS の構成
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 3decf955748b156b8eff4b5286a70e67d8ac14ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195151"
---
# <a name="configuring-http-and-https"></a>HTTP および HTTPS の構成
WCF サービスと WCF クライアントは、HTTP および HTTPS を介して通信できます。 HTTP または HTTPS の設定は、インターネット インフォメーション サービス (IIS) またはコマンド ライン ツールを使用して構成します。 WCF サービスが IIS でホストされている場合は、IIS 内で HTTP または HTTPS の設定を構成できます (inetmgr.exe ツールを使用)。 WCF サービスが自己ホスト型の場合は、コマンド ライン ツールを使用して HTTP または HTTPS の設定を構成します。  
  
 少なくとも、URL 登録を構成し、サービスで使用される URL のファイアウォール例外を追加する必要があります。  
  
 HTTP 設定の構成に使用するツールは、コンピューターで実行されているオペレーティング システムによって異なります。  
  
 実行時に[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]または[!INCLUDE[wxp](../../../../includes/wxp-md.md)]、HttpCfg.exe ツールを使用します。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] このツールは自動的にインストールされます。 実行時に[!INCLUDE[wxp](../../../../includes/wxp-md.md)]、ツールをダウンロードする[Windows XP Service Pack 2 サポート ツール](https://go.microsoft.com/fwlink/?LinkId=88606)します。 詳細については、次を参照してください。 [Httpcfg の概要](https://go.microsoft.com/fwlink/?LinkId=88605)します。  
  
 実行時に[!INCLUDE[wv](../../../../includes/wv-md.md)]Windows 7、Netsh.exe ツールを使用してこれらの設定を構成することもできます。  
  
## <a name="configuring-namespace-reservations"></a>名前空間予約の構成  
 名前空間予約では、HTTP URL 名前空間の一部に対する権限を特定のユーザー グループに割り当てます。 予約によって、名前空間のその部分でリッスンするサービスを作成する権限をユーザーに与えます。 予約は URL プレフィックスを使用します。つまり、予約は予約パスのすべてのサブパスを範囲とします。 名前空間予約では、2 つの方法でワイルドカードを使用できます。 HTTP サーバー API のドキュメントについて説明します、[ワイルドカードを含む名前空間クレーム間の解決順序](https://go.microsoft.com/fwlink/?LinkId=94841)します。  
  
 実行中のアプリケーションは、同様の要求を作成して、名前空間登録を追加できます。 名前空間の同じ部分について、登録と予約の間で競合が発生します。 予約で指定された解決順序に従って登録の優先順位があります、[ワイルドカードを含む名前空間クレーム間の解決順序](https://go.microsoft.com/fwlink/?LinkId=94841)します。 この場合、実行中のアプリケーションがクレームを受信する動作が、予約によってブロックされます。  
  
### <a name="running-windows-xp-or-server-2003"></a>Windows XP または Windows Server 2003 を実行している場合  
 使用して、`httpcfg.exe set urlacl`名前空間の予約を変更するコマンド。 [Windows サポート ツールのドキュメント](https://go.microsoft.com/fwlink/?LinkId=94840)Httpcfg.exe ツールの構文について説明します。 名前空間の一部に対する予約権限を変更するには、管理特権または名前空間のその部分の所有権が必要です。 最初は、ローカル管理者が HTTP 名前空間全体を所有しています。  
  
 `set urlacl` オプションを使用する Httpcfg コマンドの構文を次に示します。  
  
```console  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /a ACL  
```  
  
 `/u` を使用する場合には、`set urlacl` パラメーターが必要です。 このパラメーターには、実行された予約のレコード キーとして動作する完全修飾 URL を含む文字列を指定します。  
  
 `/a` を使用する場合には、`set urlacl` パラメーターも必要です。 このパラメーターには、SDDL (Security Descriptor Definition Language) の形式によるアクセス制御リスト (ACL) を含む文字列を指定します。  
  
 このコマンドの使用例を次に示します。  
  
```console  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Windows Vista、Windows Server 2008 R2、または Windows 7 を実行している場合  
 [!INCLUDE[wv](../../../../includes/wv-md.md)]、Windows Server 2008 R2、または Windows 7 を実行している場合は、Netsh.exe ツールを使用します。 このコマンドの使用例を次に示します。  
  
```console  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 このコマンドにより、DOMAIN\ユーザー アカウントについて指定した URL 名前空間の URL 予約が追加されます。  詳細については、netsh コマンドの種類を使用してキーを押して、コマンド プロンプトでの「netsh http add urlacl」を入力します。  
  
## <a name="configuring-a-firewall-exception"></a>ファイアウォールの例外の構成  
 HTTP 経由の通信を行う WCF サービスを自己ホストする際は、例外をファイアウォール構成に追加して、特定の URL を使用した着信接続を可能にする必要があります。 詳細については、次を参照してください[(Windows 7) の Windows ファイアウォールでポートを開く。](https://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>SSL 証明書の構成  
 SSL (Secure Sockets Layer) プロトコルは、クライアントとサーバー上で証明書を使用して暗号化キーを格納します。 サーバーは、クライアントがサーバーの ID を検証できるように接続時に SSL 証明書を提供します。 また、サーバーはクライアントに証明書を要求して、接続の両側で相互認証を実行することもできます。  
  
 証明書は、接続の IP アドレスとポート番号に基づいて集中ストアに格納されます。 特別な IP アドレス 0.0.0.0 は、ローカル コンピューターの任意の IP アドレスに一致します。 証明書ストアでは、パスを基準にした URL を区別しません。 同じ IP アドレスとポートの組み合わせを持つサービスは、そのサービスの URL でのパスが異なる場合でも証明書を共有する必要があります。  
  
 手順については、次を参照してください。[方法。SSL 証明書でポートを構成](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)します。  
  
## <a name="configuring-the-ip-listen-list"></a>IP リッスン一覧の構成  
 HTTP Server API は、ユーザーが URL を登録すると、IP アドレスとポートだけにバインドします。 既定では、HTTP Server API は、コンピューターのすべての IP アドレスに対して、URL でポートにバインドします。 その IP アドレスとポートの組み合わせにバインドしている HTTP Server API をアプリケーションが使用していない場合、競合が発生します。 IP リッスン一覧には、WCF サービスの一部のマシンの IP アドレス、ポートを使用するアプリケーションと共存させることができます。 IP リッスン一覧にエントリがある場合、HTTP Server API は、その一覧に指定されている IP アドレスだけにバインドします。 IP リッスン一覧を変更するには、管理特権が必要です。  
  
### <a name="running-windows-xp-or-server-2003"></a>Windows XP または Windows Server 2003 を実行している場合  
 httpcfg ツールを使用して IP リッスン一覧を変更します。次に例を示します。 [Windows サポート ツールのドキュメント](https://go.microsoft.com/fwlink/?LinkId=94840)httpcfg.exe ツールの構文について説明します。  
  
```console  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Windows Vista または Windows 7 を実行している場合  
 netsh ツールを使用して IP リッスン一覧を変更します。次に例を示します。  
  
```console  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>その他の構成設定  
 <xref:System.ServiceModel.WSDualHttpBinding> を使用すると、クライアント接続では、名前空間予約と Windows ファイアウォールに対応できる既定値が使用されます。 双方向接続のクライアント ベース アドレスをカスタマイズする場合、クライアント上で HTTP 設定を行い、新しいアドレスに一致させる必要があります。  
  
 HTTP Server API には、HttpCfg からは使用できない高度な構成設定があります。 この設定は、レジストリで管理され、HTTP Server API を使用するシステムで実行中のすべてのアプリケーションに適用されます。 これらの設定については、次を参照してください。 [IIS 用の Http.sys レジストリ設定](https://go.microsoft.com/fwlink/?LinkId=94843)します。 ほとんどのユーザーは、この設定を変更する必要がありません。  
  
## <a name="issues-specific-to-windows-xp"></a>Windows XP に固有の問題  
 IIS では、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上でのポート共有がサポートされていません。 IIS が実行されていると、WCF サービスが同じポートを持つ名前空間を使用しようとした場合、WCF サービスを開始に失敗します。 IIS と WCF どちらも、既定ポート 80 を使用します。 サービスのいずれかのポート割り当てを変更するか、IP リッスン一覧を使用して、WCF サービスを IIS で使用されていないネットワーク アダプターに割り当てます。 IIS 6.0 以上では、HTTP Server API を使用できるように設計が変更されています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.WSDualHttpBinding>
- [方法: SSL 証明書を使用してポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
