---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d5b07617617ac28e4f7f72bc23a96b45a85dff75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047978"
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> クラスは、プログラムによって制御できる HTTP プロトコル リスナーを提供します。 リスナーは、<xref:System.Net.HttpListener> オブジェクトの有効期間にわたってアクティブで、アプリケーション内で実行されます。  
  
## <a name="httpsys"></a>HTTP.SYS  
 <xref:System.Net.HttpListener> クラスは、Windows のすべての HTTP トラフィックを処理するカーネル モード リスナーである HTTP.sys の上に構築されています。 HTTP.sys は、接続管理、帯域幅の調整、および Web サーバーのログ記録を提供します。 SSL 証明書の追加には `HttpCfg.exe` ツールを使用します。 詳細については、[サーバー](https://go.microsoft.com/fwlink/?LinkID=178285) ドキュメントで、[HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) ツールのドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [HTTP サーバー](https://go.microsoft.com/fwlink/?LinkID=178285)
- [インターネット インフォメーションにおけるセキュリティ強化](https://go.microsoft.com/fwlink/?LinkID=178286)
- [HttpListener ASPX ホスト アプリケーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=179560)
- [HttpListener テクノロジのサンプル](https://go.microsoft.com/fwlink/?LinkID=179558)
- [ネットワーク プログラミングのサンプル](network-programming-samples.md)
