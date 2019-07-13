---
title: アプリケーション開発での PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 4cd0d739e58cd252213e8d5c16d29cc612338df6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178140"
---
# <a name="pnrp-in-application-development"></a>アプリケーション開発での PNRP
Windows Vista では、ネットワーク アプリケーションは、簡単な PNRP アプリケーション プログラミング インターフェイス (API) を通して名前発行および名前解決機能にアクセスできます。  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>ピア名解決プロトコルの実装  
 簡略化された PNRP API では、名前とアドレスを登録するためにクラウドを明示的に指定することはありません。PNRP コンポーネントは、参加する適切なクラウドと、クラウド内で公開するアドレスを、自動的に決定ます。  
  
 Windows Vista の非常に簡略化された PNRP 名前解決では、Windows Sockets 関数 getaddrinfo() に PNRP 名が組み込まれています。 PNRP を使って名前を IPv6 アドレスに変換する場合、getaddrinfo() 関数を使って完全修飾ドメイン名 (FQDN) name.prnp.net を解決できます。ここで name は解決されるピア名です。 pnrp.net ドメインは、PNRP 名前解決のために Windows Vista で予約されているドメインです。  
  
 PeerToPeer アプリケーション間でのメッセージの受け渡しは、依然として PeerChannel や WCF の[大規模データとストリーミング](https://go.microsoft.com/fwlink/?LinkID=179652)などの、基盤のアーキテクチャによって処理されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.PeerToPeer>
