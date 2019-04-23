---
title: TCP-UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: e074a487c39dfaf1c4704f9dadf7ed8e430fb630
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172550"
---
# <a name="tcp-udp"></a>TCP-UDP
アプリケーションは、<xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.UdpClient> クラスで伝送制御プロトコル (TCP) サービスとユーザー データグラム プロトコル (UDP) サービスを利用できます。 これらのプロトコルのクラスは <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> クラスの上に構築され、データ転送の詳細を処理します。  
  
 このプロトコル クラスは **Socket** クラスの同期メソッドを利用し、ネットワーク サービスへの簡単なアクセスを提供します。状態情報を維持する必要がなく、プロトコル特有のソケットを設定するための詳細を知る必要もありません。 非同期 **Socket** メソッドを使用するには、<xref:System.Net.Sockets.NetworkStream> クラスが提供する非同期メソッドを使用できます。 プロトコル クラスでは公開されない **Socket** クラスの機能にアクセスするには、**Socket** クラスを使用する必要があります。  
  
 **TcpClient** と **TcpListener** は、**NetworkStream** クラスを利用するネットワークを表します。 <xref:System.Net.Sockets.TcpClient.GetStream%2A> メソッドを利用してネットワーク ストリームを返し、ストリームの <xref:System.Net.Sockets.NetworkStream.Read%2A> メソッドと <xref:System.Net.Sockets.NetworkStream.Write%2A> メソッドを呼び出します。 **NetworkStream** にはプロトコル クラスの基盤となるソケットがありません。そのため、閉じてもソケットに影響はありません。  
  
 **UdpClient** クラスはバイトの配列を利用し、UDP データグラムを保持します。 <xref:System.Net.Sockets.UdpClient.Send%2A> メソッドを利用してデータをネットワークに送信し、<xref:System.Net.Sockets.UdpClient.Receive%2A> メソッドを利用し、入ってくるデータグラムを受信します。  
  
## <a name="see-also"></a>関連項目

- [TCP サービスの使用](../../../docs/framework/network-programming/using-tcp-services.md)
- [UDP サービスの使用](../../../docs/framework/network-programming/using-udp-services.md)
- [ネットワーク上でストリームを使用する](../../../docs/framework/network-programming/using-streams-on-the-network.md)
- [非同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [非同期クライアント ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)
