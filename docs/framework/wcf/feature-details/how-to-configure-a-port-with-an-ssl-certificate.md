---
title: '方法: SSL 証明書を使用してポートを構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: fb5ca2c5e0040ed86c9f51323f390d625d658903
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622939"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>方法: SSL 証明書を使用してポートを構成する
自己ホスト型 Windows Communication Foundation (WCF) サービスを作成するときに、<xref:System.ServiceModel.WSHttpBinding>クラスを使用してトランスポート セキュリティ、X.509 証明書でポートを構成することも必要があります。 自己ホスト型サービスを作成するのでなければ、インターネット インフォメーション サービス (IIS) でサービスをホストできます。 詳細については、次を参照してください。 [HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)します。  
  
 ポートを構成する場合に使用するツールは、コンピューターで実行されているオペレーティング システムによって異なります。  
  
 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] または [!INCLUDE[wxp](../../../../includes/wxp-md.md)] を実行している場合は、HttpCfg.exe ツールを使用します。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では、このツールは自動的にインストールされています。 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]、ツールをダウンロードする[Windows XP Service Pack 2 サポート ツール](https://go.microsoft.com/fwlink/?LinkId=88606)します。 詳細については、次を参照してください。 [Httpcfg の概要](https://go.microsoft.com/fwlink/?LinkId=88605)します。 [Windows サポート ツールのドキュメント](https://go.microsoft.com/fwlink/?LinkId=94840)Httpcfg.exe ツールの構文について説明します。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] を実行している場合は、Netsh.exe ツールを使用します。これは既にインストールされています。  
  
 このトピックでは、次のようなさまざまな手順を実行する方法について説明します。  
  
- コンピューターの現在のポート構成を確認する。  
  
- 証明書の拇印を取得する (次の 2 つの手順に必要)。  
  
- SSL 証明書をポート構成にバインドする。  
  
- SSL 証明書をポート構成にバインドし、クライアント証明書をサポートする。  
  
- ポート番号から SSL 証明書を削除する。  
  
 コンピューターに格納されている証明書を変更するには、管理特権が必要です。  
  
### <a name="to-determine-how-ports-are-configured"></a>ポートの構成を確認するには  
  
1. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]または[!INCLUDE[wxp](../../../../includes/wxp-md.md)]、HttpCfg.exe ツールを使用して、現在のポート構成を表示するを使用して、**クエリ**と**ssl**スイッチ、次の例に示すようにします。  
  
    ```  
    httpcfg query ssl  
    ```  
  
2. [!INCLUDE[wv](../../../../includes/wv-md.md)] で現在のポート構成を表示するには、Netsh.exe ツールを使用します。次に例を示します。  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>証明書の拇印を取得するには  
  
1. 証明書 MMC スナップインを使用して、クライアント認証を目的として含む X.509 証明書を検索します。 詳細については、「[方法 :MMC スナップインで証明書を表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)します。  
  
2. 証明書の拇印にアクセスします。 詳細については、「[方法 :証明書のサムプリントを取得](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)します。  
  
3. 証明書のサムプリントを、メモ帳などのテキスト エディターにコピーします。  
  
4. 16 進文字の間にある空白をすべて削除します。 たとえばエディターの "すべて置換" 機能を使用して、空白を空文字列に置き換えるとよいでしょう。  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>SSL 証明書をポート番号にバインドするには  
  
1. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] または [!INCLUDE[wxp](../../../../includes/wxp-md.md)] で証明書をポート番号にバインドするには、HttpCfg.exe ツールを SSL (Secure Sockets Layer) ストアに対して "set" モードで使用します。 このツールは、次のように、拇印を使用して証明書を識別します。  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **-I**スイッチの構文には`IP`:`port`し、コンピューターのポート 8012 に証明書を設定するツールに指示します。 "0.0.0.0" の部分は、必要に応じて、コンピューターの実際の IP アドレスに置き換えてください。  
  
    - **-H**証明書の拇印を指定します。  
  
2. [!INCLUDE[wv](../../../../includes/wv-md.md)] では、Netsh.exe ツールを使用します。次に例を示します。  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - **Certhash**パラメーターは、証明書のサムプリントを指定します。  
  
    - **Ipport**パラメーターは、IP アドレスとポートを指定し、同様に機能、 **-i**説明した Httpcfg.exe ツールのスイッチ。  
  
    - **Appid**パラメーターは、所有するアプリケーションを識別するために使用できる GUID です。  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>SSL 証明書をポート番号にバインドし、クライアント証明書をサポートするには  
  
1. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] または [!INCLUDE[wxp](../../../../includes/wxp-md.md)] では、トランスポート層で X.509 証明書を使用して認証するクライアントをサポートするには、前と同じ手順を実行しますが、次のように HttpCfg.exe に追加のコマンド ライン パラメーターを指定します。  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F**スイッチの構文には`n`n は 1 ~ 7 の数値です。 前の例のように 2 を指定すると、クライアントはトランスポート層で認証することになります。 値として 3 を指定すると、クライアント証明書が有効になり、それらの証明書が Windows アカウントに対応付けられます。 他の値については、HttpCfg.exe のヘルプ機能を参照してください。  
  
2. [!INCLUDE[wv](../../../../includes/wv-md.md)] では、トランスポート層で X.509 証明書を使用して認証するクライアントをサポートするには、前と同じ手順を実行しますが、次のように追加のパラメーターを指定します。  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>ポート番号から SSL 証明書を削除するには  
  
1. HttpCfg.exe または Netsh.exe ツールを使用して、コンピューター上のすべてのバインディングのポートと拇印を確認します。 情報をディスクに出力するには、次の例のようにリダイレクト文字 ">" を使用します。  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]または[!INCLUDE[wxp](../../../../includes/wxp-md.md)]を使用して、HttpCfg.exe ツールを使用して、**削除**と**ssl**キーワード。 使用して、 **-i**スイッチを指定、 `IP`:`port`数、および **-h**拇印を指定するスイッチ。  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. [!INCLUDE[wv](../../../../includes/wv-md.md)] では、Netsh.exe ツールを使用します。次に例を示します。  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>例  
 次のコードは、トランスポート セキュリティを設定した <xref:System.ServiceModel.WSHttpBinding> クラスを使用して、自己ホスト型サービスを作成する方法を示します。 アプリケーションを作成する際、アドレス中にポート番号を指定してください。  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
