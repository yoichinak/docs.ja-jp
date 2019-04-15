---
title: プラグ可能なプロトコルのプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: d14eb426c8e142f56d9f024dcbf37a1d2d78664d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072342"
---
# <a name="programming-pluggable-protocols"></a>プラグ可能なプロトコルのプログラミング
抽象クラスの <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> は、プラグ可能なプロトコルの基礎を提供します。 アプリケーションでは、<xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> からプロトコル固有のクラスを派生することにより、使うプロトコルを指定しなくても、インターネット リソースにデータを要求して応答を読み取ることができます。  
  
 プロトコル固有の <xref:System.Net.WebRequest> を作成するには、その前に Create メソッドを登録する必要があります。 <xref:System.Net.WebRequest> の静的 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> メソッドを使って、特定のインターネット スキーム、スキームとサーバー、またはスキームとサーバーとパスに対する要求のセットを処理するための、<xref:System.Net.WebRequest> の子孫を登録します。  
  
 ほとんどの場合は、<xref:System.Net.WebRequest> クラスのメソッドとプロパティを使ってデータを送受信できます。 ただし、プロトコル固有のプロパティにアクセスする必要がある場合は、<xref:System.Net.WebRequest> を特定の派生クラス インスタンスに型キャストできます。  
  
 プラグ可能なプロトコルを利用するには、<xref:System.Net.WebRequest> の子孫で、プロトコル固有のプロパティを設定する必要がない既定の要求-応答トランザクションを提供する必要があります。 たとえば、HTTP 用の <xref:System.Net.WebRequest> クラスを実装する <xref:System.Net.HttpWebRequest> クラスは、既定で `GET` 要求を提供し、Web サーバーから返されたストリームを含む <xref:System.Net.HttpWebResponse> を返します。  
  
## <a name="see-also"></a>関連項目

- [WebRequest からの派生](../../../docs/framework/network-programming/deriving-from-webrequest.md)
- [WebResponse からの派生](../../../docs/framework/network-programming/deriving-from-webresponse.md)
- [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)
- [方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
