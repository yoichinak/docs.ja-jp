---
title: '方法: ソケットを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 0bbdab11201171bf8d730276c7f94cbc5317acdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101121"
---
# <a name="how-to-create-a-socket"></a>方法: ソケットを作成する
ソケットを使用してリモート デバイスと通信するには、ソケットをプロトコルとネットワーク アドレスの情報を使用して事前に初期化する必要があります。 <xref:System.Net.Sockets.Socket> クラスのコンストラクターには、アドレス ファミリ、ソケットの種類、およびソケットが接続を行うために使用するプロトコルの種類を指定するパラメーターがあります。  
  
## <a name="example"></a>例  
 次の例では、インターネットなどの TCP/IP ベースのネットワーク上で通信するために使用できるソケットを作成します。  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 TCP ではなく UDP を使用するには、次の例のように、プロトコルの種類を変更します。  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> 列挙体では、ネットワーク アドレスを解決するために **Socket** クラスで使用される標準のアドレス ファミリを指定します (たとえば、**AddressFamily.InterNetwork** メンバーは IPv4 アドレス ファミリを指定します)。  
  
 <xref:System.Net.Sockets.SocketType> 列挙体ではソケットの種類を指定します (たとえば、**SocketType.Stream** メンバーは、フロー制御付きでデータを送受信するための標準のソケットを示します)。  
  
 <xref:System.Net.Sockets.ProtocolType> 列挙体では、**Socket** での通信時に使用するネットワーク プロトコルを指定します (たとえば、**ProtocolType.Tcp** はソケットが TCP を使用することを示し、**ProtocolType.Udp** はソケットが UDP を使用することを示します)。  
  
 **Socket** が作成されたら、リモート エンドポイントへの接続を開始したり、リモート デバイスから接続を受信したりすることができます。  
  
## <a name="see-also"></a>関連項目

- [クライアント ソケットの使用](../../../docs/framework/network-programming/using-client-sockets.md)
- [リッスン (ソケットで)](../../../docs/framework/network-programming/listening-with-sockets.md)
