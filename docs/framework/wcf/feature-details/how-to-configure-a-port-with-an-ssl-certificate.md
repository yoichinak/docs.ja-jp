---
title: '方法 : SSL 証明書を使用してポートを構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185107"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>方法 : SSL 証明書を使用してポートを構成する

トランスポート セキュリティを使用する<xref:System.ServiceModel.WSHttpBinding>クラスを使用して、自己ホスト型の Windows 通信基盤 (WCF) サービスを作成する場合は、X.509 証明書を使用してポートを構成する必要もあります。 自己ホスト型サービスを作成するのでなければ、インターネット インフォメーション サービス (IIS) でサービスをホストできます。 詳細については、「 [HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)」を参照してください。  
  
 ポートを構成する場合に使用するツールは、コンピューターで実行されているオペレーティング システムによって異なります。  
  
 Windows Server 2003 を実行している場合は、HttpCfg.exe ツールを使用します。 Windows Server 2003 では、このツールがインストールされています。 詳細については、「 [Httpcfg の概要](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))」を参照してください。 [Windows サポート ツールのドキュメント](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10))では、Httpcfg.exe ツールの構文について説明します。  
  
 Windows Vista を実行している場合は、既にインストールされている Netsh.exe ツールを使用します。
  
> [!NOTE]
> コンピュータに保存されている証明書を変更するには、管理者特権が必要です。  
  
## <a name="determine-how-ports-are-configured"></a>ポートの構成方法を決定する  
  
1. Windows Server 2003 または Windows XP では、次の例に示すように、HttpCfg.exe ツールを使用して、**クエリ**と**SSL**スイッチを使用して現在のポート構成を表示します。  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. Windows Vista では、次の例に示すように、Netsh.exe ツールを使用して現在のポート構成を表示します。  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>証明書の拇印を取得する  
  
1. 証明書 MMC スナップインを使用して、クライアント認証を目的として含む X.509 証明書を検索します。 詳細については、「 [方法: MMC スナップインを使用して証明書を参照する](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)」をご覧ください。  
  
2. 証明書の拇印にアクセスします。 詳細については、「[方法: 証明書のサムプリントを取得する](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)」を参照してください。  
  
3. 証明書のサムプリントを、メモ帳などのテキスト エディターにコピーします。  
  
4. 16 進文字の間にある空白をすべて削除します。 たとえばエディターの "すべて置換" 機能を使用して、空白を空文字列に置き換えるとよいでしょう。  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>SSL 証明書をポート番号にバインドする  
  
1. Windows Server 2003 または Windows XP では、セキュリティで保護されたソケット レイヤー (SSL) ストアの "設定" モードで HttpCfg.exe ツールを使用して、証明書をポート番号にバインドします。 このツールは、次のように、拇印を使用して証明書を識別します。  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **i**スイッチは :`IP``port`という構文を持ち、コンピュータのポート 8012 に証明書を設定するようにツールに指示します。 "0.0.0.0" の部分は、必要に応じて、コンピューターの実際の IP アドレスに置き換えてください。  
  
    - **h**スイッチは、証明書の拇印を指定します。  
  
2. Windows Vista では、次の例に示すように、Netsh.exe ツールを使用します。  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - **certhash**パラメーターは、証明書の拇印を指定します。  
  
    - **ipport**パラメーターは、IP アドレスとポートを指定し、説明されている Httpcfg.exe ツールの **-i**スイッチと同じように機能します。  
  
    - **appid**パラメーターは、所有するアプリケーションを識別するために使用できる GUID です。  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>SSL 証明書をポート番号にバインドし、クライアント証明書をサポートする  
  
1. トランスポート層で X.509 証明書を使用して認証するクライアントをサポートするために、Windows Server 2003 または Windows XP では、上記の手順に従いますが、次の例に示すように、追加のコマンド ライン パラメータを HttpCfg.exe に渡します。  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **f**スイッチの構文`n`は、n が 1 から 7 までの数値です。 前の例のように 2 を指定すると、クライアントはトランスポート層で認証することになります。 値として 3 を指定すると、クライアント証明書が有効になり、それらの証明書が Windows アカウントに対応付けられます。 他の値については、HttpCfg.exe のヘルプ機能を参照してください。  
  
2. Windows Vista では、トランスポート層で X.509 証明書を使用して認証するクライアントをサポートするには、次の例に示すように、上記の手順に従いますが、追加のパラメータを使用します。  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>ポート番号から SSL 証明書を削除する  
  
1. HttpCfg.exe または Netsh.exe ツールを使用して、コンピューター上のすべてのバインディングのポートと拇印を確認します。 情報をディスクに出力するには、次の例に示すように、リダイレクト文字 「>」を使用します。  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Windows Server 2003 または Windows XP では、**削除**キーワードと**SSL**キーワードを指定して HttpCfg.exe ツールを使用します。 **i**スイッチを使用して :`IP``port`番号を指定し **、-h**スイッチを使用して拇印を指定します。  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. Windows Vista では、次の例に示すように、Netsh.exe ツールを使用します。  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>例  

 次のコードは、トランスポート セキュリティを設定した <xref:System.ServiceModel.WSHttpBinding> クラスを使用して、自己ホスト型サービスを作成する方法を示します。 アプリケーションを作成する際、アドレス中にポート番号を指定してください。  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
