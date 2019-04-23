---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d3fecb9fe78ca54f68d3c5a97dae5d5dd9fbb28d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075419"
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
- [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)
